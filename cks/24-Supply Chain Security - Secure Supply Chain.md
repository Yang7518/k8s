## K8s and Container Registries
- Private registry with Kubernetes
![](./images/24/private%20registry%20with%20kubernetes.PNG)
- Use Image Digest
   - List all image registries used in the whole cluster 
```concole
kubectl get pod -A -o yaml | gerp "image:" | grep -v "f:"
```
   - Use Image digest for kube-apiserver
![](./images/24/use%20image%20digest%20for%20kube-apiserver.PNG)
   - Whitelist Registries with OPA
     - Only inmages from docker.io and k8s.gcr.io can be used
       - install opa  
         kubectl create -f https://raw.githubusercontent.com/ killer-sh/cks-course-environment/master/course-content/opa/gatekeeper.yaml

       - opa resources  
         https://github.com/killer-sh/cks-course-environment/tree/master/course-content/supply-chain-security/secure-the-supply-chain/whitelist-registries/opa
   - ImagePolicyWebhook
![](./images/24/image%20policy%20webhook%2001.PNG)
     - Investigate ImagePolicyWebhook  
       Use it to the point where is callc an external service 
![](./images/24/image%20policy%20webhook%2002.PNG)
![](./images/24/image%20policy%20webhook%2003.PNG)
![](./images/24/image%20policy%20webhook%2004.PNG)
![](./images/24/image%20policy%20webhook%2005.PNG)
![](./images/24/image%20policy%20webhook%2006.PNG)
![](./images/24/image%20policy%20webhook%2004.PNG)

