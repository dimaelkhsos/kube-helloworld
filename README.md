# kube-helloworld

The helloworld app I created using simple NodeJS express application that returns “Hello World” when invoked.

This repo contains helloworld-app folder, which contains the Dockerfile and all application needed files. (I already have it as an image in my docker hub account dimagomaa/helloworldnodejs)

Steps to get the app working: (in case you want to build it from beginning)
1. docker build .
2. to test it
docker run -p [HostPort]:[ContainerPORT] -it [DockerImageId]
docker run -p 3000:3000 -it df2d0cf7d454

It will print the message "Hello World Application running on port 3000!!!"

If you want to test it from browser, just use any port forwarding tunnel, and open your browser localhost:3000
It will print "Hello World from Dima NJ Application" in red color.

3. Tag the docker image
docker tag [Image_ID] [DockerHubUsername]/[DockerHubRepoName]
docker tag df2d0cf7d454 dimagomaa/helloworldnodejs

4. Then finally, Docker push the image:
docker push [DockerHubUsername]/[DockerHubRepoName]
docker push dimagomaa/helloworldnodejs

NOW, we can easily pull this image and run it on Kubernete.

===========================================================================================================================
# Install kubernete cluster.

Prerequisites:
- 3 CentOS 7 Servers
- Root privileges

Steps in brief:
- Kubernetes Installation
- Kubernetes Cluster Initialization
- Adding node01 and node02 to the Cluster
- Testing 
===========================================================================================================================
# Deployment file
Here you can find i created hello-world.yml deploment file, with 3 replicas. then we will see how to scale.

kubectl create -f hello-world.yml --record
kubectl get deployments
kubectl get pods
kubectl get pods -o wide

To Scale:
kubectl scale deployment helloworld-nj --replicas=10
kubectl get pods -o wide
