## Audit Logs 
![](./images/27/audit%20logs%2001.PNG)
- Why do we need Audit Logs?
   - Did someone access an important secret while it was not protected?
   - When was the last time that user X did access cluster Y?
   - Dose my CRD work properly?

- Audit Plicy Stages
![](./images/27/audit%20policy%20stages.PNG)

- API Request Stages
   - Each request can be recorded with an associated "stage". Ten known stage are:
     - RequestReceived - The stage for event genertes as soon as the audit handler receives the request, and before it is delegated down the handler chain.
     - ResponseStarted - Once the response headers are sent, but before the response body is sent. This stage is only generated for long-running requests(e.g.watch).
     - ResponseComplete - The response body has been completed and no more bytes will be sent.
     - Panic - Events generated when a panic occured.

- Audit Policy - What data to store?
![](./images/27/audit%20policy%20-%20%20what%20data%20to%20store.PNG)
  - Audit Policy Rule LEVEL
    - None - don't log events that match this rule.
    - Metadata - log request metadata(requesting user,timestamp,resource,verb,etc.)but not request or response body.
    - Request - log event metadata and request body but not response body.This does not apply for non-resource requests.
    - RequestResponse - log event metadata,requestand response bodies.This does not apply fot non-resource requests.
  - What events should be recorded and what data should these contain?
![](./images/27/audit%20policy%20-%20what%20data%20should%20be%20recorded.PNG)

- Audit Backends - Where to store all that data?
![](./images/27/audit%20backend%20-%20where%20to%20store%20all%20that%20data.PNG)

- Audit Logs - Overview
![](./images/27/audit%20logs%20-%20overview.PNG)

- Setup Audit Logs
   - Configure apiserver to store Audit Logs in JSON format
     - https://github.com/killer-sh/cks-course-environment/tree/master/course-content/runtime-security/auditing

- Restirct amount of Audit Logs to Collet
   - Restirct logged data with an Audit Policy
      - Nothing from stage RequestReceived
      - Nothing from "get","watch","list"
      - From Secrets only metadata level
      - Everything else RequestResponse level
```console
1. Change Policy file
2. Disable audit logging in apiserver,wait till restart
3. Enable audit logging in apiserver,wait tll restatt
     a. If apiserver doen't start,then check:
        /var/log/pods/kube-systems_kuba-apiserver*
4. Test the changes
```
![](./images/27/restrict%20amount%20of%20audit%20logs%20to%20collect.PNG)

