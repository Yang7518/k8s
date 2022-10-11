## mTLS - Mutual TLS
- Mutual authentication
- Two-way(bilateral) authentication
- Two parties authenticating each other at the same time
![](./images/19/mTLS%20between%20pods.PNG)
↓
![](./images/19/mTLS%20between%20pods%2002.PNG)

## ServiceMesh
![](./images/19/service%20mesh.PNG)
![](./images/19/service%20mesh%2002.PNG)
- Create a proxy sidecar which with NET_ADMIN capability
   - Create application container
```console
kubectl run app --image=bash -o yaml --dry-run=client > app.yaml -- sh -c 'ping google.com'
```
   - Create a sidecar container 
![](./images/19/service%20mesh%2003.PNG)
   - Recreate the container
