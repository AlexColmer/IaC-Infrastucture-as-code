# Terraform

## How to set up terraform

### step 1
- got to https://developer.hashicorp.com/terraform/downloads?product_intent=terraform. and install the version you need. 

### Step 2
- find the file that was downloaded and extarct it.
- cut and creat a new local file and paste it in there.
### step 3 
- press windows key and type in env and environment variable should come up.
- then you need to fin path and click `edit` and then `new`
- add the file path where you pasted terraform 
- if this is done right open up a new git bash terminla iwth admin and type `terraform --version` and you should see the version of tyerraform you just downloaded.
### Step 4
- go back to env variable and where it says user add a new file and add your ssh key pairs.  `AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY`

### Step 5
- in vs code make sure that you make a `main .tf` file. 
in that file run this code 
```
provider "aws" {
    region = "eu-west-1"
}
```

### step 7 
- to lainch an ec2 write this in the main.tf file
```
resource "aws_instance" "app_instance" {
  ami = "ami-0cc867a368804a0cc"
  instance_type = "t2.micro"
  associate_public_ip_address = true    
  tags = {
       name = "alex-tech201-terraform-app"
  }
}
```  
### Step 8
- to make sure all the synatx is correct run this code `terraform plan` 

then run `terraform apply`