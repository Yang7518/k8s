## Security Contexts
- Define privilege and access control fot Pod/Container
  - UsrID and GroupID
  - Run privileged or unprivileged
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: security-context-demo
spec:
  securityContext:   # <-- Pod Level(all containers) PodSecurityContext
    runAsUser: 1000
    runAsGroup: 3000
    fsGroup: 2000
  containers:
  - name: sec-ctx-demo
    image: busybox:1.28
    command: [ "sh", "-c", "sleep 1h" ]
    securityContext:   # <-- Container Level(pod-level override)
      allowPrivilegeEscalation: false
```
![](./images/18/security%20context.PNG)
## PrivilegeEscalation
  AllowPrivilegeEscalation controls whether a process can gain more privilege tha its parent process.  
  By default Kubernetes allows PrivilegeEscalation.  
  Privileged VS PrivilegeEscalation
  ![](./images/18/privilege%20escalation.PNG)
## PodSecurityPolicies

