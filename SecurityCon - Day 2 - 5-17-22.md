# Cloud Native SecurityCon - Day 2
Tags: #security #kubernetes

## Keynote: Why Wait? Find Cloud Risks and Threats in Real Time with Stream Detection
*Presenters: Loris Degioanni, Sysdig*

Tags: #security #tools 

### Falco
- https://falco.org/
- https://falco.org/community/
- Falco is the security camera for modern ages
- Is possible now to write plugins for Falco
	- For example: Audit, detect a console login without MFA...
- Monitor configuration changes
- Detect infiltrations
- Strange behaviors

#### Stream Detection Advantages
- Responsive, real time alerts
-  No data store or data movement
- Full coverage
- Efficient
- Scalable
- Affordable

## Keynote: Evolutions in data privacy: threats and opportunities 
*Presents: Kirsten A. Newcomer, Red Hat*

Tags: #security #encryption

- All sectors are involved
- Healthcare suffered the most from security incidents

### Encryption data continues to be keys
- OpenSSL 3 and FIPS 140-3
- Tekton chains - Attested toolchain with Tekton Chains
- Confidential containers 
	- https://github.com/confidential-containers
- Sigstore
- Keylime - Remote attestation
	- https://keylime.dev/

### Homomorphic encryption
- Ability to do computations on encrypted data without access to the secret key
- Results remain encrypted

### Post-Quantum cryptography aka PQC
- Expected in 2023-2026 timeframe
- Quantum Cumputing can break encryption we used today in as little as 10 seconds


## Vanquishing Vulnerabilities in Valencia
*Presenters: Alba Ferri Fitó, Sysdig & Eric Smalling, Synk*

Tags: #security 

### Minimize footprint
Don't give hackers more tools to expand their exploits
Stick to smallest containers and do not provide tools!

### Layer Housekeeping
Understand how layers work at build and run-time

### Build strategies
Multistage, repeatable builds, standardized labeling, alternative tools

### Secure Supply Chain
Know where image come from. Only CI should push to registries !!!

## Security Context
- Don't container as root
- Don't do privileged containers
- Drop capabilites
	-  Most apps don't need event Linux capabilityes, dropping all and allow only what's need
- Read only Root Filesystem
	- Immutability makes exploiting hard


### Network Policy
- Start with nothing working, only DNS for service discory
- Whitelist only what you need !
- Limit the connection way like Webapp to DB and not DB to Webapp

### Admission Controller
#### Enforcement
- OPA (GateKeeper)
- Kyverno
- Pod Security Admission
	-  https://kubernetes.io/docs/concepts/security/pod-security-admission/

### Shift security to left and Shield to the right
- Be aware of the behavior of exploits
- Runtime container security
	- If we know the normal behavior of our container we can be alterted when you have unsual behaviors
	- Intercept data
	- Filter and apply rules
	- Send alerts in real time
	- Use simple, common rules language
- We needed to be alterted as soon as possible

### Runtime intelligence
- What libraries are loaded ?
- Which have known exploits ?
- Do you have a fix?

## First Steps to Full Lifecycle Security with Open Source Tools
*Presents: Rory McCune & Anais Urlichs, Aqua Security*

[[First Steps to Full Lifecycle Security with Open Source Tools - HackMD.pdf]]

- https://aquasecurity.github.io/trivy/v0.28.0/

### Security Scanning Process
- Before every thing, you need to deploy a scanner to understand what is inside your cluster

### Vulnerability Scanning
- It's a useful way of assessing base images

## LockC
https://github.com/lockc-project/lockc

## Recommandations - Bad things in cluster
- No Network rules
- No Resource Limits
- Privileged mode
- Root user
- Misplaced credentials
- Risky capabilities
	- Cluster had applications running with dangerous Linux capabilities

## Real time security - eBPF for preventing attacks
*presenters: Liz Rice*

Book: Report - What is eBPF ?

### Runtime security - security in real time
- Detecting malicious activity in real time
- Reporting when malicious events occur
- Preventing them

### What activiy do we care about ?
- Network traffic
- File activity
- Running executables
- Changing privileges

**All these activities require support from the kernel**

### How could we spot this activity ?
- LD_PRELOAD
- ptrace
- seccomp
- eBPF



