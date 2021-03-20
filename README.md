# CONFIGURING HAPROXY LB AND BACKEND INSTANCES USING ANSIBLE

In this project we configure haproxy load balancer on one vm and backend httpd server on other vm’s. Then we use jinja templating in the haproxy config file which will automatically update the config file with the ip of the new backend if any new backend server is launched. All of this will be done entirely from our workstation using ansible.

To configure this architecture we use ansible playbooks. We create one playbook for configuring haproxy and one playbook for backend servers. 

In the ansible inventory we create two groups one for load balancer and other for backend server. 

Everytime we wish to add a new server to the backend we simply add the ip in the inventory and from here only it will be updated in the haproxy config file. We create a copy of haproxy config file in our workstation and edit it. In place of backend servers we create a loop which will pick the ips from the backend group in the ansible inventory. 
