# Setup-SSH-Between-Ansible-And-Nodes

This repository contain code to deploy the sample application on linux instances

# Directory Structure

1.  configs - contain environment specific variable
2.  inventories - contains inventory file for each environment
3.  groups_vars - contains common variables across environments
4.  roles - This will have subfolders like nginx,add_devops_user,and tomcat

    a) tomcat - this folder will have files related to the installation of tomcat

            - files (This will contain files which you want to copy to to your destination servers)

            - handlers ( This is used to start/stop the services)

            - templates (This will contain template files)

            - tasks ( playbook to install the software)

    b) add_devops_user - This folder will have files related to the setup of initial user

    c) nginx - this folder will have files related to the installation, configuration of nginx, and deployment of a static website

            - files (This will contain files which you want to copy to to your destination servers)

            - handlers ( This is used to start/stop the services)

            - templates (This will contain template files)

            - tasks ( playbook to install the software)

5.  main.yml - This is the main file which will execute roles in the playbook

# How to Run the Playbook

```
ansible-playbook main.yml -i inventories/dev/hosts --user ubuntu --key-file /home/ubuntu/your_pem_file.pem -e '@configs/dev.yml'

ansible-playbook main.yml -i inventories/dev/hosts --user devops --key-file /home/devops/.ssh/id_rsa -e '@configs/dev.yml'


```

# References
