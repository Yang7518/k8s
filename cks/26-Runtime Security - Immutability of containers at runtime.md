## Imumutability
- Container won't be modified during it's lifetime
![](./images/26/imuutability%2001.PNG)
![](./images/26/imuutability%2002.PNG)

## Enforce on Container Image Level
![](./images/26/enforce%20on%20container%20image%20level.PNG)
- Make manual changes to container - StartProbe
![](./images/26/pod%20startup%20timeline.PNG)
- Enforce Read-Only Root Filesystem
   - Using SecurityContexts and PodSecurityPolicies
![](./images/26/enforce%20read-only%20root%20filesystem.PNG)

## StartupProbe for Immutability
- Use StartupProbe to remove touch and bash from container
![](./images/26/startupprobe%20for%20immutability.PNG)

## Enforce RO-filesystem
- Create PodSecurityContext to make filesystem Read-Only(Ensure some directories are still writable using emptyDir volume)  
![](./images/26/enforce%20ro-filesystem%2001.PNG)
![](./images/26/enforce%20ro-filesystem%2002.PNG)