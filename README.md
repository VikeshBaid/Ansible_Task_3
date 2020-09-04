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
  - calls the role for load balancer
  - roles should be define in the /etc/ansible/roles directory as by default ansible looks roles at this path.
  - user can also define roles in desired location by adding **roles_path** keyword with path to roles directory in **ansible.cfg** file.

3. **webserver_setup script**
  - same as lb_script file, contains role for webserver
  - roles should be define in the /etc/ansible/roles directory as by default ansible looks roles at this path.
  - user can also define roles in desired location by adding **roles_path** keyword with path to roles directory in **ansible.cfg** file.

4. **hosts directory**
  - contains ec2.py file whcih is used to fetch the ip address of hosts(instance) dynamically and pass it to ansible playbook.
  - also contains ec2.ini file which can be used to modify the request sent by ec2.py file to AWS.
  - To know more on dynamic inventory used by Ansible [click here](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html#inventory-script-example-aws-ec2)

5. **roles directory**
  - contains two roles
    1. lbserver
    2. webserver
  - **lbserver** role has all the tasks required to setup, configure and run **HAproxy software** in tasks directory.
  - **lbserver** role has a template file in Template directory for HAproxy configuration, named **haproxy.cfg** which is used to setup Target Ip dynamically.
  - **lbserver** role has handler task in handler directory which triggers when notify is called from a task.
  - **webserver** role has all the tasks required to setup, configure and run **httpd software** in tasks directory.
