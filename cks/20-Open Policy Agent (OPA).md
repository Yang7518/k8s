## Open Policy Agent - OPA
- Create a new pod
![](./images/20/create%20a%20new%20pod.PNG)
- The Open Policy Agen(OPA) os an open source, general-purpose policy engin that enables unified,context-aware policy enfocement across the entire stack
   - Not Kubernetes specific
   - Easy implementation of policies(Rego language)
   - Works with JSON/YAML
   - In K8s it uses Admission Controlers
   - Does not know concepts like pods or deployments

## OPA Gatekeeper
![](./images/20/opa%20gatekeeper%2001.PNG)
![](./images/20/opa%20gatekeeper%2002.PNG)

## Admission Controllers
![](./images/20/admission%20controlers.PNG)

## OPA - Deny All
- Install OPA
![](./images/20/opa%20install%2001.PNG
- Install the template and Constraint
![](./images/20/opa%20install%2002.PNG)

## OPA - Namespaces need labels
- All namespaces created need to hace the label "cks"
   - https://github.com/killer-sh/cks-course-environment/tree/master/course-content/opa/namespace-labels

## OPA - Deployment replica count
- All deployments created need to hace minimum replica count
  - https://github.com/killer-sh/cks-course-environment/tree/master/course-content/opa/deployment-replica-count

## Rego Playground
- https://play.openpolicyagent.org
- https://github.com/BouweCeunen/gatekeeper-policies
 



