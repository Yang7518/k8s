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
- PodSecurityPolicy was deprecated in Kubernetes v1.21, and removed from Kubernetes in v1.25
- Cluster-level resource
- Controls under which security conditions a Pod has to run
![](./images/18/pod%20security%20policies%2001.PNG)
- Fileds
![](./images/18/pod%20security%20policies%2002.PNG)
- Enable
![](./images/18/pod%20security%20policies%2003.PNG)
- Create a PodSecurityPolicy to always enforce no allowPrivilegeEscalation(Practice)
   - Change kube-apiserver's manifests
   - Create PSP
   - Create a role and a rolebinding to use PSP
```yaml
apiVersion: extensions/v1beta1
kind: PodSecurityPolicy
metadata:
  name: privileged
  annotations:
    seccomp.security.alpha.kubernetes.io/allowedProfileNames: '*'
spec:
  privileged: false
  allowPrivilegeEscalation: false
  allowedCapabilities:
  - '*'
  volumes:
  - '*'
  hostNetwork: true
  hostPorts:
  - min: 0
    max: 65535
  hostIPC: true
  hostPID: true
  runAsUser:
    rule: 'RunAsAny'
  seLinux:
    rule: 'RunAsAny'
  supplementalGroups:
    rule: 'RunAsAny'
  fsGroup:
    rule: 'RunAsAny'
   ```  
