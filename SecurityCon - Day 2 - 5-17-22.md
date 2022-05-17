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

