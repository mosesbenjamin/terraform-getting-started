﻿# terraform-getting-started

__m3__
- terraform init
- terraform validate
- terraform plan -out m3.tfplan
- terraform apply "m3.tfplan"
- terraform destroy

__m4__

#First run
- terraform init
- terraform plan -out m4.tfplan
- terraform apply "m4.tfplan"

- terraform show
- terraform output

#Second run
#Rename the files to use the updated config
- ren modulefour-start.tf modulefour-start.tf.rename
- ren modulefour-update.tf.rename modulefour-update.tf

- terraform plan -out m4.tfplan
- terraform apply "m4.tfplan"

- terraform destroy

#Set the files back
- ren modulefour-start.tf.rename modulefour-start.tf
- ren modulefour-update.tf modulefour-update.tf.rename

__m5__
- terraform init
- terraform plan -out m5.tfplan
- terraform apply "m5.tfplan"

- terraform destroy

__m6__
#Functions testing
# You actually need to initialize the config before terraform console will work
- terraform init

- terraform console
- min(42,5,16)
- cidrsubnet(var.network_address_space, 8, 0)
- cidrhost(cidrsubnet(var.network_address_space, 8, 0),5)
- lookup(local.common_tags, "BillingCode", "Unknown")
- lookup(local.common_tags, "Missing", "Unknown")
- local.s3_bucket_name

#Configuration command

- terraform plan -out m6.tfplan
- terraform apply "m6.tfplan"

- terraform destroy

__m7__
- terraform init
- terraform workspace new Development
- terraform plan -out development.tfplan
- terraform apply "development.tfplan"

- terraform workspace new UAT
- terraform plan -out uat.tfplan
- terraform apply "uat.tfplan"

#Don't forget to remove from tfvars, variables, and resource provider
# For PowerShell
$env:AWS_ACCESS_KEY_ID="AWS_ACCESS_KEY_ID"
$env:AWS_SECRET_ACCESS_KEY="AWS_SECRET_ACCESS_KEY"

# For Bash
- export AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID
- export AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY

- terraform workspace new Production
- terraform plan -out production.tfplan
- terraform apply "production.tfplan"

-terraform destroy

- terraform workspace select UAT
- terraform destroy

- terraform workspace select Development
- terraform destroy

__m8__
- terraform init
- terraform workspace new Development
- terraform plan -out development.tfplan
- terraform apply "development.tfplan"

- terraform destroy
