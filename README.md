# IaC (infrastructure as code)

## What is it
- is the managing and provisioning of infrastructure through code instead of through manual processes. Helps us codify everything 
## Why do we use it 
- IaC can help your organization manage IT infrastructure needs while also improving consistency and reducing errors and manual configuration
## Where do we use it 
- With IaC, configuration files are created that contain your infrastructure specifications, which makes it easier to edit and distribute configurations
## when do we use it 
- It helps you to align development and operations because both teams can use the same description of the application deployment, supporting a DevOps approach. The same deployment process should be used for every environment, including your production environment.
## how do we use it 
- 
## Confiduration management 
- In the technology world, configuration management is an IT management process that tracks individual configuration items of an IT system.
## Orchetration 
- Orchestration. Orchestration means arranging or coordinating multiple systems
## Tools
- ![Alt text](../Images/IaC%20Tools.png)
## who is using it
- 
## Terraform- Ansible
## on prem - Hybrid - Cloud
## What other tools are avliable 
## push vs pull config 
- In the pull method, the to be configured server pulls its configuration from the controlling server whereas the push method, the controlling server pushes the configuration to the destination system.

# How to get three machines running and ansible on the controller machine 

## Step 1
- open a new vscode window and add a vagranfile 
## Step 2 
- in the vagrant file add this code for all three machines 
```
# ansible-tech201


# -*- mode: ruby -*-
 # vi: set ft=ruby :
 
 # All Vagrant configuration is done below. The "2" in Vagrant.configure
 # configures the configuration version (we support older styles for
 # backwards compatibility). Please don't change it unless you know what
 
 # MULTI SERVER/VMs environment 
 #
 Vagrant.configure("2") do |config|
 # creating are Ansible controller
   config.vm.define "controller" do |controller|
     
    controller.vm.box = "bento/ubuntu-18.04"
    
    controller.vm.hostname = 'controller'
    
    controller.vm.network :private_network, ip: "192.168.33.12"
    
    # config.hostsupdater.aliases = ["development.controller"] 
    
   end 
 # creating first VM called web  
   config.vm.define "web" do |web|
     
     web.vm.box = "bento/ubuntu-18.04"
    # downloading ubuntu 18.04 image
 
     web.vm.hostname = 'web'
     # assigning host name to the VM
     
     web.vm.network :private_network, ip: "192.168.33.10"
     #   assigning private IP
     
     #config.hostsupdater.aliases = ["development.web"]
     # creating a link called development.web so we can access web page with this link instread of an IP   
         
   end
   
 # creating second VM called db
   config.vm.define "db" do |db|
     
     db.vm.box = "bento/ubuntu-18.04"
     
     db.vm.hostname = 'db'
     
     db.vm.network :private_network, ip: "192.168.33.11"
     
     #config.hostsupdater.aliases = ["development.db"]     
   end
 
 
 end
```

## Step 3
- Vagrant up to get all three machines running
## Step 4
- when SSH into all three machines and run `sudo apt update and upgarde in them` 
## step 5
- intsall ansible with these lines of code 
```
sudo apt-get install software-properties-common
```
```
sudo apt-add-repository ppa:ansible/ansible
```
```
sudo apt-get install ansible -y
```
- This will install ansible