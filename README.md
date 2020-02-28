# Overview

This is a demonstration project for using Jenkins and Ansible together to manage simple CI/CD pipelines while allowing for scaling to complicated and complex deployment and delivery scenarios. By using these two tools together, development teams have the ability to handle any scale of complex application deployment.

# Requirements
This demonstration project requires an Ansible AWX (or Tower) instance installed that has network access to the artifact repository (e.g. Bintray) and the host on which the application is to be run. Additionally, the AWX server should have access to a host on which it can run integration tests. This can be any host Ansible can manage. This is normally a Linux environment. This will represent your continuous deployment pipeline. 

Next, a Jenkins instance is required which can reach your source code repository (e.g. GitHub) your Artifact Repository (e.g. Bintray), and the Ansible AWX server to kick off deployment jobs when the application has been published. This will represent your Continuous Integration pipeline.

It is often a good practice to setup 3 linux servers:
* Delivery host - Linux host with Docker CE installed to run both AWX and Jenkins in Docker containers
* Application Host - Linux host with Java installed
* Test Host - Linux host with Java installed

## Jenkins
First off, you need a Jenkins instance. It is probably easiest to use the [latest Jenkins Docker](https://hub.docker.com/_/jenkins/) image from Docker Hub. When I'm running from my Windows laptop, I usually use the following to get things started:
```
$ docker run --name jenkins -p 8080:8080 -p 50000:50000 -v c:\jenkins:/var/jenkins_home jenkins
```
This places all my Jenkins data in the `c:\jenkins` directory. For me this is fine. You may want to place it in your user directory.

## Ansible AWX
You will need an Ansible AWX instance running somewhere. Depending on your environment, you can take a variety of approaches. While I'm at my client's site, Internet access is limited and I have to use their internal Cloud infrastructure. That mean I have a set of Ansible plays that set up the environment while I'm on site.

## Starting the Web Application
To perform testing of the application on the local workstation, run it from within the Maven build tool: 
```
$ mvn spring-boot:run
```
