# Provider Configuration

The required_providers block in Terraform is used to declare and specify the required provider configurations for your Terraform module or configuration. It allows you to specify the provider name, source, and version constraints.

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.0"
    }
    azurerm = {
      source  = "hashicorp/azurerm"
      version = ">= 2.0, < 3.0"
    }
  }
}
```


Why specify a version?

Avoid unexpected updates: If Terraform upgrades to a newer provider version, it might introduce breaking changes.
Ensure consistency: Everyone on your team will use the same provider version.

terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}

# Create a VPC
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

Authentication:

provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}


% export AWS_ACCESS_KEY_ID="anaccesskey"
% export AWS_SECRET_ACCESS_KEY="asecretkey"
% export AWS_REGION="us-west-2"


These values can be given as
1. parametrs in providers block
2. as environmental variables
3. shared configuartion and credential files $HOME/.aws/config  $HOME/.aws/credentials
   
   

