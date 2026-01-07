# Day 01 - IaC Basics

## Topics Covered
- What is Infrastructure as Code?
- Benefits of IaC
- Terraform overview
- HCL (HashiCorp Configuration Language)
- Providers and Resources

## Basic Terraform Example
```hcl
# Provider configuration
provider "aws" {
  region = "us-east-1"
}

# Resource definition
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  
  tags = {
    Name = "WebServer"
  }
}
```

## Commands
```bash
terraform init
terraform plan
terraform apply
terraform destroy
```

## Notes
