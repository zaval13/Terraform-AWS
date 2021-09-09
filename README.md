## Deploying cotainerized Wordpress site on AWS EC2 instance. Create Grafana and Graphite containers + Collectd

#### Jenkins: 
- pull project from Github
- run jobs for Terraform and Ansible
- run job for deploy containers with Wordpress site & DB
#### Terraform: 
- Deploy AWS EC2 instanse, setup security group, add ellastic IP, open ports.
#### Ansible: 
- install Docker, Docker Compose
- create Grafana & Graphite containers, install Collectd
- start containers with Woerdpress & DB. (Docker Compose)
