# Cloud Native SecurityCon
Tags: #security #kubernetes


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

