# Ansible - Task 3

## Technology Used
1. Ansible v2.9
2. HAproxy software(for creating Load Balancer Server)
3. httpd software(for creating webserver)
4. Base OS used in both servers is RedHat Enterprise Linux, version 8

## Description of Task

Lauched a Infrastructure in which a Load Balancer is managing three Target system. Webserver is running on the three target system. For creating a load balancer HAproxy software is used which internally uses Round Robin algorithm.

1. **ec2\_provision script**
  - Ansible Module Used: **ec2**
  - creates 1 Load Balancer instance and 3 Websever instance

2. **lb\_setup script**

