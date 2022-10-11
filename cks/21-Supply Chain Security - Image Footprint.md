## Containers and Docker
![](./images/21/containers.PNG)
![](./images/21/docker%20images%2001.PNG)
![](./images/21/docker%20images%2002.PNG)

## Reduce Image Footprint
- Look at an external Golang Dockerfile and reduce the image footprint via Muti-Stage Build
   - Build image and Run
```concole
docker build -t app .
docker run app
```
![](./images/21/reduce%20image%20footprint.PNG)  
Only the last Stage can be saved

## Secure and hardening Images
- Use Specific package versions
- Don't run as root
- Make filesystem read only
- Remove shell access
![](./images/21/secure%20and%20hardening%20images.PNG)

## Best Practices for writing Dockerfiles
- https://docs.docker.com/develop/develop-images/dockerfile_best-practices/