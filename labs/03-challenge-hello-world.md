# Challenge: Hello World

In this challenge you will write a hello world application, in the language of your choice, and deploy it to Kubernetes.

Perform the following steps:

* Write an application that responds to web requests with "hello world" on port 8000
* Package the application in a Docker container image
* Push the container image to a Docker repository
* Create a Kubernetes deployment for the application. Limit the CPU to half a CPU core.
* Expose the application using a LoadBalancer
* Set up a Kubernetes autoscaler to scale the application based on CPU usage. Set the min and max
