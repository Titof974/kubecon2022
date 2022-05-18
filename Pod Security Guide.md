# Pod Security guide
*presenter: Lachlan Evenson, Microsoft*

Tags: #security #kubernetes 

## Concepts
### What is pod security ?
- Build-in
- Evaluates pod specifications against a predefined set of Pod Security Standards
- Applied at namespaced level when pods are created
 
 ### Why pod security ?
 - Restrict pod privileges
 - Reduce surface of attack
 - Predefined
 - Supports and encourages Kubernetes best practices
 - Performs validation only
 - Pod security doesnt support mutation

### Other similar ecosystem tooling
More complexe functionnalities or mutation:
	- Kyverno
	- Gatekeeper

### Elements of Pod Security
- Built-in admission controller
- Tree policy levels known as **Pod Security**
	- privileged - open and unrestricted
	- baseline - convers known privilege escalations hwile minimizing restrictions
	- restricted - highly restricted; hardening against known and unknwon privilege escalations. May cause problems...
- Applied via labels on namespace resources which allows for granular per-namespace policy selection


- Policies are apply by mode
- 3 modes:
	- enforce - will be stricly blocked
	- audit - will be recorded
	- warn - warn message but don't affected whether the pod is allowed

* Policies are applied to a namespace via labels

* Start with warn and after that enforce
	* The typical uses for warn are to get ready for a future change where you want to enforce a different policy

