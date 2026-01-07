# Terraform Infrastructure Project

## Overview
Complete infrastructure provisioning using Terraform.

## Architecture
- VPC with public/private subnets
- EC2 instances
- RDS database
- S3 buckets
- Load balancer
- Security groups

## Project Structure
```
terraform/
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
├── modules/
│   ├── vpc/
│   ├── ec2/
│   ├── rds/
│   └── s3/
└── environments/
    ├── dev/
    ├── staging/
    └── prod/
```

## Usage
```bash
# Initialize
terraform init

# Plan
terraform plan -var-file=environments/dev/terraform.tfvars

# Apply
terraform apply -var-file=environments/dev/terraform.tfvars

# Destroy
terraform destroy
```

## Notes
