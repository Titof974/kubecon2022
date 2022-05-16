# Cloud Native SecurityCon
Tags: #security #kubernetes

- Software Supply Chain Best Practices : [[CNCF_SSCP_v1.pdf]]

## DevSecOps and the art of not ending up on the front page
*Presenter: Fabio Rapposelli - Senior Staff Engineer, VMware @fabiorapposelli*

Tags: #sbom #security  #tools

- Generate SBOM
- "Sec" into "Devops" -> SLAS / OWASP (tools/framework)
	- Other tools: [in-toto](https://in-toto.io/), [cartographer](https://cartographer.sh/), [sigstore](https://www.sigstore.dev/), Open Policy Agent...

# Fuzzing the CNCF landscap
*Presenter: adalogics.com, Adam Korczynski, David Korczynski*

[[Fuzzing the CNCF landscape-final-slides.pdf]]

Tags: #security #tools #fuzzing

## Fuzzing ?
- Automated testing
- https://owasp.org/www-community/Fuzzing
- Fuzzing is not random testing
- Fuzzers are conceptually only test-case generators. They generate inputs that trigger code paths, i.e. they are not bug identifiers as such but rather execution path identifiers.

#### Normal test vs Fuzzing
Normal test:
```
MyAPI(input1)
MyAPI(input1)
MyAPI(input1)
```

Fuzing:
```
while(true)
	MyAPI(Fuzzer.GenerateInput())
```

### Open source fuzzing with OSS-Fuzz
- https://github.com/google/oss-fuzz
- ClusterFuzz Lite (lighter than OSS-Fuzz)
	- https://google.github.io/clusterfuzzlite/

### CNCF projects being fuzzed
- https://github.com/cncf/cncf-fuzzing
- Istio will come in the fuzzed projects !

# Dissecting the Discovery of the 0-Day Supply Chain Vulnerability in Argo CD
*Presenter: Moshe Zioni, Apiiro*

https://apiiro.com/blog/malicious-kubernetes-helm-charts-can-be-used-to-steal-sensitive-information-from-argo-cd-deployments/

Tags: #CI #CD #tools 

## What is Argo CD ?
- https://argo-cd.readthedocs.io/en/stable/ 
- An open-source GitOps CD tool under CNCF

## CVE-2022-24348
- NOT the most dangerous
- Targets critical supply chain junction - Popular Continous Delivery infrastructure.
- Utilization of payload by a native supply chain artifact (Helm Chart)

![[Pasted image 20220516105314.png]]


## Discovery - Research Approach (3-Steps)
### Explore
- Familiarize yourself with the project, documentation, codebase...
- Build a model to play with... tweak around... 
- Run by tutorials for peripheral views

### Realize Use Cases
- Basic Flows...
- Try different ways to achieve the same things - UX, API...
- Security concerns and hardening reveals on the "not-use" cases
- Plugins and extended usage


### Dive Into Mechanics
- Understand why it's like this
- Find the issue, the history of the implementation (like for example on github...)

# CTF
*Presenters: Lewis @denhamparry, James @jpts_, andy @sublimino*

- Best way to learn about security
- https://github.com/kubernetes-simulator/simulator - Kubernetes Security Training Platform - Focussing on security mitigation
- Taskmaster - https://cloud-native.slack.com

# Security Champions: The What, Why, and How 
*Presenters: Ann Marie Fred, Red Hat*

- Cost of a data breach ~ Ignorance is not a defense
- 2021:
	-  24% companies has been hacked or suspected to 
	- Average data breach: 4.24 Millions $
	- Over 18k CVE
	- 66 Zero Day vulnerabilities

# Protect the Pipe! A Policy-based Approach for Securing CI/CD Pipelines 
*Presenters: Shripad Nadgowda, IBM Research & Jim Bugwadia, Nirmata*

Tags: #security #tools #kubernetes 

## Stack
### Tekton
https://tekton.dev/
Cloud native CD

### In-toto
https://in-toto.io/

### Sigstore
https://www.sigstore.dev/
Signing software artifact

### Kyverno
https://kyverno.io/
- Policy engine designed for kubernetes
- Automate security
- Work with in-toto

# TUF Maintainer Panel Discussion
*Presenters: Moderated by Andrew Krug, Datadog; Asra Ali, Google; Marina Moore, NYU; Trishank Karthik Kuppusamy, Datadog; & Jussi Kukkonen, VMware*

Tags: #security #tools #toolbox

## What is TUF ?
https://theupdateframework.io/

- A framework for securing software update systems
- Multiple tools for security

# VEX! or... How to Reduce CVE Noise With One Simple Trick!
*Presents: Frederick Kautz, Anthem*

Tags: #security 

## Cost to an Attacker
- Risks and Rewarfs
- Reward / Time
- Reward / Financial cost (value of the attack)
- Reward / Penalty if caught
- Reward / Chance of being caught

## Cost to a Defender
- Single Loss Expectancy
	- SLE = Assets Value * Exposure value
- Annualized loss Expectancy
	- ALE = ANnual Rate of Occurence * SLE
- Residual Value
	- RV = Asset Value - Cost to Protect

## VEX
### Vulnerability Modeling Gap
- SBOMs are Static
- Vulnerabilities are Dynamic

### CVEs
- Several major efforts aiming to link SBOMs to CVE
- CVEs don't tell the whole story -> Not everything is affected by its vulnerabilities!
- CVE noise in large environments limits the effectiveness of these programs

### Working around the gap
- Upgrade in any cases (costs?)
- Customers may mitigate the vulnerability with secondary controls
- Customers may accept the risk
- Customers may eliminate the risk by disabling the product
- Customers may also transfer the risk via insurance...

### What is Vex ?
 VEX stands for Vulnerability Exploitability eXchange.
 It's a profile which allows for organizations to make statements about whether a product is **affected** by a vulnerability.

![[Pasted image 20220516145022.png]]

- SBOMS tell you what is your infrastructure
- CVEs tell you what vulnerabilities are in your environment
- VEX tell you which vulnerability you are affected by

- No Database for the moment


# Detecting Data Exfiltration on the Edge with Pixie 
*Presenters: Zain Asgar, New Relic*

Tags: #tools  #monitoring

Not for production, just some ideas

## Data Exfiltration Risks
- Leaks of informations like credit cards, SSNs, phone numbers etc...
- Cost money

## What is Pixie ?
https://px.dev/

- Performance debugging without manual instrumentation
	- CPU, Memory, Network
	- Message spans with latency, contents
	- Performance profiles (flamegraphs)
- Zero intrumentation: No manual intrumentation zith eBPF
- Distributed architecture with in-memory datastore
- Scriptable Python/Pandas interface

# What’s Inside Your Container Image? How to Audit All the Dependencies in Your software Supply-Chain
*Presenters: Steve Judd, Jetstack*

[[Auditing-dependencies-in-containers.pdf]]

## What is The Software Supply Chain ?
- What make up our product ?
- Where did the components come from ?
- Where are components used ?
- Who has control over the components ?


## What did we want to achieve ?
- Component inventory
- Vulnerability tracking
- License compliance
- Discoverability (Single point to look at the informations)

## How ? 5 - Steps to dependency auditing
- 1 - Use only a trusted Image registry
	- Much more control on the image
	- Use your own cache registry (Artifactory, Nexus, Harbor, etc...)
	- Not be dependend
- 2 - Generate Image SBOMs (Tool: Syft)
	- https://github.com/anchore/syft
- 3 - Evaluate the Image (Tool: Dependency Track)
	- https://github.com/DependencyTrack/dependency-track
- 4 - Approve / Deny / Mitigate
	- If an Image is compliant:
		- Sign & Push SBOM (Tools: cosign)
		- Sign Image
		- Create, sign & push compliance attestation
- 5 - Maintain a Dependency Inventory

# Using CNCF Best Practices for Software Supply Chain to Guide and Enhance Your Security Posture
*Presenters: Ryan Gibbons, 3m & Conor Rogers, Stelligent*

[[CNSC-EU-2022-RG_CR_v0.2.pdf]]

## The Situation
- Lack of awarness of software supply chain security practices
	- Knowledge gaps
	- Data gaps
- Limited guidance on how to secure the software supply chain tooling

![[Pasted image 20220516155112.png]]

## SSCP - The Principles
- 1 - Trust
- 2 - Automation
- 3 - Clarity
- 4 - Mutual Authentication

## SSCP - The Practices
- 1- Securing The source code
- 2 - Securing Materials
- 3 - Securing Build Pipelines
- 4 - Securing the Artefacts
- 5 - Securing the Deployments

# The Unexpected Demise of Open Source Libraries
*Presents: Liran Tal, Synk*

- Reinstalling packages from registries is inefficient and non-deterministic

Tools: Verdacio
https://verdaccio.org/fr-fr/

