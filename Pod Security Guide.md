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
	- baseline -  known privilege escalations while minimizing restrictions
	- restricted - highly restricted; hardening against known and unknown privilege escalations. May cause problems...
- Applied via labels on namespace resources which allows for granular per-namespace policy selection


- Policies are apply by mode
- 3 modes:
	- enforce - will be strictly blocked
	- audit - will be recorded
	- warn - warn message but don't affected whether the pod is allowed

* Policies are applied to a namespace via labels

* Start with warn and after that enforce
	* The typical uses for warn are to get ready for a future change where you want to enforce a different policy

* The audit mode logs to the cluster audit log

## Pod security in Action
- Check if pod security is enabled
* Use `--dry-run=server` to test
* When restricted policy is used you need to explicitly set field in the pod, no default value !
* No container running as root
	* Use securityContext -> runAsUser: 65534 ??
* metrics:
	* pod_security_evaluations_total to get the number of time the policies was it
	* `kubectl get --raw /metrics | grep pod_security_evaluations_total`

## Next step
- Use warn and audit on existing namespaces
	- Use dry-run to evaluate all resources in a namespace when applying an enfoce label to a namespace
- Set warn to the same level as enforce so that users get early feedback
- Make a goal to get all workload namespaces to baseline standard
	- Start with audit and move towards enforce

