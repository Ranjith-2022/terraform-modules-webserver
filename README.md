# Terraform Modules Webserver

## Support of Multiple Environments with Terraform

This project aims to provide support for deploying webserver infrastructure using Terraform across multiple environments. Below are the commands and steps to set up and manage the infrastructure.

## Architecture

![image](https://github.com/Ranjith-2022/terraform-modules-webserver/assets/114111480/fa0ad836-910d-4539-8101-dca1a64389dd)

### Commands

#### Step 1: Terraform Installation

```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
```

#### Step 2: Create S3 Bucket for Backend State File

Create an S3 bucket named "terraform-modules-1" to store the Terraform backend state file.

#### Step 3: Configuring Dev - Network

```bash
cd project/dev/network
terraform init
terraform plan
terraform apply --auto-approve
```

#### Step 5: Creating SSH Key for Dev Webserver

```bash
ssh-keygen -t rsa -f project-dev
```

#### Step 6: Configuring Dev - Webserver

```bash
cd ../webserver
terraform init
terraform plan
terraform apply --auto-approve
```

#### Step 7: Configuring Prod - Network

```bash
cd ../../prod/network
terraform init
terraform plan
terraform apply --auto-approve
```

#### Step 8: Creating SSH Key for Prod Webserver

```bash
ssh-keygen -t rsa -f project-prod
```

#### Step 9: Configuring Prod - Webserver

```bash
cd ../webserver
terraform init
terraform plan
terraform apply --auto-approve
```

#### Step 10: Deconstructing Developed Configuration

```bash
terraform destroy --auto-approve
cd ../network
terraform destroy --auto-approve
cd ../../dev/webserver
terraform destroy --auto-approve
cd ../network
terraform destroy --auto-approve
```

This README provides guidance on setting up and managing the infrastructure for both development and production environments using Terraform.
