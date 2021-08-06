## Deploying cotainerized Wordpress site on AWS EC2 instance. 

#### Docker: 
- create image with Jenkins, Terraform, Ansible
- start container with volume for data persistence
#### Jenkins: 
- pull project from Github
- run jobs for Terraform and Ansible
- run job for deploy containers with Wordpress site & DB
#### Terraform: 
- Deploy AWS EC2 instanse, setup security group, add ellastic IP, open ports.
#### Ansible: 
- install Docker, Docker Compose
- create Grafana & Graphite containers, install Collectd
- start containers with Woerdpress & DB.
