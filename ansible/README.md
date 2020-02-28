# Overview

This is an Ansible project to install AWX and containerized Jenkins on Red Hat systems. It is intended to make installation of AWX and Jenkins simple for experimentation, particularly in the AEP cloud.

AWX provides a web-based user interface, REST API, and task engine built on top of [Ansible](https://github.com/ansible/ansible). It is the upstream project for [Tower](https://www.ansible.com/tower), a commercial derivative of AWX. 

If you want to experiment with [Ansible Tower](https://www.ansible.com/tower), this project will give you the environment you need with the ability to use everything in your future [Tower](https://www.ansible.com/tower) installation.

Jenkins is added to this project to demonstrate the ability of using Jenkins and Ansible together in CI/CD pipelines.



# Notes

You have to setup Jenkins after the install

1. Copy over the root cert, and mannually add to the java cacert file.
1. log into the system as admin
1. Defune the proxy in the Jenkins configuration confirgre system -. manage plugins -> advanced
1. Add all the basic plugins

