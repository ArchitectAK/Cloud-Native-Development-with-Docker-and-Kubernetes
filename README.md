# Cloud-Native-Development-with-Docker-and-Kubernetes

While the vast majority of Node.js apps are deployed and run in the cloud, few leverage all that modern cloud computing platforms have to offer. If you're looking to take the next step in your cloud computing journey,

## Learning objectives

- Using Node.js in the cloud
- Creating a Node.js app
- Building a production Dockerfile
- Deploying an app to Kubernetes using Helm
- Adding self-healing capabilities
- Building custom charts and graphs
- Adding support for metrics and request tracking

## What is Cloud Native ?

Lets undersnatd this by answering few questions

### What does "cloud native" mean?

- Before we can describe cloud native, we first need to talk about cloud computing, what it provides and how to use that to understand what cloud native really means.
- Why cloud computing?
  - Wikipedia describes cloud computing as "the on-demand availability of cloud system resources."
  - It also helps to minimize upfront IT infrastructure costs because you don't need to buy and provision hardware for the amount of work that you are banked to do, you only need to provide hardware and buy resource for what you are currently using.
  - So cloud computing provides a managed platform that's infinitely scalable and always available and compute on demand.
- As we move into the cloud, microservices become a possibility.
  - Martin Fowler, one of the thought leaders for microservices, describes them as "a suite of small services "that run on their own "and communicate with each other "using lightweight mechanisms"
  - They should be independently deployable, which means they are also independently scalable.
- What about cloud native technologies?

  - The Cloud Native Computing Foundation or CNCF refers to cloud native technologies as "technologies that empower you "to build scalable applications "which are deployed to hybrid public or private clouds."
  - They also describe them as being "loosely coupled systems which are resilient, "manageable and observable."
  - InfoWorld talk about them in terms of "an approach to building "and running applications."They exploit the advantages of cloud computing."
  - A key part being there, that cloud native applications exploit the advantages of the cloud computing delivery model.

- So let's look at what this means. Let's say I'm building an application on my laptop. If I take that application and I just deploy it to a cloud, it's not cloud native, it's just cloud hosted.
- For it to be a cloud native application,
  - it needs to be a small, lightweight service,
  - it needs to be independently deployable and scalable,,
  - most importantly, it needs to exploit the capabilities that the cloud provides.

### Node.js in the cloud

- Microservices are described as being small, lightweight, and independently scalable, and that means there are some performance characteristics that can help determine whether a language is a good fit for microservice development.
- One of those is IO and the reason for that, is that microservices are designed to communicate with other microservices, and that communication requires the ability to work with `IO Speed`.
- Another criteria that's useful for microservices is `startup`, and this is because startup speed affects your ability to do scaling and to restart after a failure.
- So the greater your startup speed, the quicker you will restart after a failure and the quicker you'll be able to add additional instances and react to additional load.
- Microservices are described as being small, so their memory footprint is important. Particularly so in clouds where most clouds charge according to the amount of memory that you are using. So the more memory you use, the more you'll be charged by the cloud provider.

### Clound Native Node.js

- The CloudNativeJS project enables you to
  - package your application for cloud.
  - exploit the cloud itself, providing automatic restarts, scaling, metrics and observability
  - write Cloud Native Node.js

## Woeking on the app

- [Sample app](app)
- [Added Dockrfile](app/Dockerfile) -
  - We've already run our application locally, but now we're going to package it as a docker image.
  - This takes our application, which is running on our laptop, and packages it, so that it can run in a self-contained container.
  - That container has everything that the application needs in order to be able to run.
  - This includes an image of a Linux operating system. In this case Ubuntu 16 04. Along with Ubuntu System Libraries, a version of Node.js.
  - The cloud native JS project provides docker file templates as part of its open source projects.
- [Build a dev and debug Dockerfile](app/run-debug) -
- [Build a production Dockerfile](app/Dockerfile-run) -
- Tagging and version control

## Deploying to Kubernetes

### Docker vs Kubernetes

- App can be used to run the Docker container on another machine, and that other machine could be a cloud.
- But docker only have a single instance of our application running in a single container. To go beyond that this is where Kubernetes comes in.
- Kubernetes will let us run multiple instances of the same container and load balance any incoming request across the multiple instances.
- Kubernetes will also allow us to connect to other things. That might be something as simple as a database or it might be another application or microservice.
- Kubernetes will also let us to integrate with cloud capabilities.
- Kubernetes is the container orchestrator that was originally developed to Google and which was subsequently open sourced and donated to the CNCF, the Cloud Native Computing Foundation.
- Kubernetes provides support for deploying multiple containers and replicas.
- Kubernetes also provides support for service discovery load balancing, self healing which means restarting on failures, as well as secret and configuration management and allowing you to roll out, roll back and scale horizontally to more instances based on load.

### Helm chart

- To deploy app to Kubernetes, we're going to use Helm.
- Helm is the package manager for Kubernetes.
- Helm describes itself as helping you define, install and upgrade even the most complex Kubernetes application.
- Helm provides us with the ability to package our app, along with all of the configuration it needs, into a chart. That chart then describes how our app should be deployed and run.
- Helm Hub
  - Helm Hub is a search engine that Helm itself provides that lets you find charts to install existing software.
