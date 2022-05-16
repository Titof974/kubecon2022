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
