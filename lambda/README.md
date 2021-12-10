# Lambda-Terraform-Python

This repo will automate much of the process to deploy a lambda function with a Python code that will print out the user's IP upon visiting the API gateway URL.

## Technology Stack
- Terraform
- AWS
- Lambda
- API-Gateway

## Features

- Deploy's a small Python code that simply prints the user's IP upon visiting the API-gateway

# Requirements
- AWS CLI
- Terraform
- Python3

# Downloads

## Terraform
https://learn.hashicorp.com/tutorials/terraform/install-cli
• Ensure that your system is up to date, and you have the gnupg, software-properties-common, and curl packages installed. You will use these packages to verify HashiCorp's GPG signature, and install HashiCorp's Debian package repository.

- `$ sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl`

• Add the HashiCorp GPG key.
- `$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -`

• Add the official HashiCorp Linux repository.
- `$ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"`

• Update to add the repository, and install the Terraform CLI.
- `$ sudo apt-get update && sudo apt-get install terraform`

## AWS
• Prerequisetes
- `$ sudo apt install unzip`

AWS setup
• Then download AWS
- `$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"`
- `$ unzip awscliv2.zip`
- `$ sudo ./aws/install`

• Remember to remove the zip afterwards with 
- `$ rm -r zip-file-name`

• Remember to update if doesn’t let you download package/install
- `$ sudo apt-get update`

### Python3
• Depending on your distro of Linux your likely to have Python already installed.
• Check version with the following cmd:
- `$ python3 --version`

• If you don't have it install you can install Python3 with the following:
- Update your local Repositories.
    - `$ sudo apt update`
- Then upgrade packages installed on your local machine.
    - `$ sudo apt -y upgrade` 
- Its possible that you may see a python version now so try this one more time.
    - `$ python3 --version`
- If still no success we can now apply the python3 install cmd.
    - `$ sudo apt install python3` 

# Prerequisites
AWS IAM user with Administrator Access permissions

## AWS Configurations

• After creating your user that has programmatic access to with permissions to services you will be deploying on AWS, you head to your terminal and issue the cmd. 
- `$ aws configure --profile iam-user`

## Changes needed to files
### terraform/

`variable.tf` 
- Variables
- `region = your specific region`
- `profile = your IAM user`
- `lambda_iam_name = custom iam name`
- `lambda_function_name = custom function name`

`lambda.tf` 
- Data `lambda-zip`
    - `source_file = file location/name, if you didn't move the file then you can leave it as is.`

- Resource `lambda-function`
    - `runtime = your custom runtime if you change the the lambda file, if not you can leave it as is.`


# Procedure

-You cd into the project directory
    - `$ cd lambda`
-Next you can issue the simple terraform commands
    - `$ terraform init`
    - `$ terraform plan`
    - `$ terraform apply`
        -`$ yes`

Afterwards you can head to the AWS console and see the lambda function. You can then test it by heading to the AWS service api-gateway and copy the url to the broswer. Once arrived you'll see it print your own IP.

# Clean up
All done? 
- Let's clean up with terraform command 
- `$ terraform destory -auto-approve`
