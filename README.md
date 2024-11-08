# terraform-s3-backend

A Terraform module to create an S3 bucket and DynamoDB table for use as a backend for Terraform state files.

## Usage

Create a `main.tf` file in your project directory with the following content:

```terraform
terraform {
  backend "local" {}

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "5.74.0"
    }
  }
}

provider "aws" {
  # partial configuration, reads keys from env vars
  region = var.aws_region
}

module "example_backend" {
  source           = "<path to module>"
  app_name         = "<app_name>"
  bucket_name      = "<bucket_name>"
  environment_name = "<environment_name>"
  table_name       = "<table_name>"
}
```
