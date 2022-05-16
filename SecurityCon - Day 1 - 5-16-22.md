# Cloud Native SecurityCon
Tags: #security #kubernetes
[[Fuzzing the CNCF landscape-final-slides.pdf]]

## DevSecOps and the art of not ending up on the front page
*Presenter: Fabio Rapposelli - Senior Staff Engineer, VMware @fabiorapposelli*

Tags: #sbom #security  #tools

- Generate SBOM
- "Sec" into "Devops" -> SLAS / OWASP (tools/framework)
	- Other tools: [in-toto](https://in-toto.io/), [cartographer](https://cartographer.sh/), [sigstore](https://www.sigstore.dev/), Open Policy Agent...

# Fuzzing the CNCF landscap
*Presenter: adalogics.com, Adam Korczynski, David Korczynski*

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
- Istio will come in the fuzzed project !
