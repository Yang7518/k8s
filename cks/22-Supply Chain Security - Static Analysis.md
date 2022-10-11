## Static Analysis
- Look at source code and text files
- Check Against rules
- Enforce rules

## Static Analysis Rules
![](./images/22/static%20analysis%20rules.PNG)

## Kubesec
- We use Kubesec to perform static analysis
   - Using the Kubesec public docker image
   - docker run -i kubesec/kubesec:512c5e0 scan /dev/stdin < pod.yaml

## Conftest - OPA
- Unit test framework for kubernetes configurations
- Use Rego language

## OPA conftest K8s Deployment
- Use conftest to check a k8s example
- 
