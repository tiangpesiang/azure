# Create storage account using Terraform 

# main.tf
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 4.0" # Use a modern version
    }
  }
}

provider "azurerm" {
  features {} # Required for the provider to function
}

# 2. Create a Resource Group
resource "azurerm_resource_group" "example" {
  name     = "rg-demo-resources"
  location = "centralindia"
}

# 3. Create a Storage Account
resource "azurerm_storage_account" "example" {
  name                     = "stexampleaccount123" # Must be globally unique
  resource_group_name      = azurerm_resource_group.example.name
  location                 = azurerm_resource_group.example.location
  account_tier             = "Standard"
  account_replication_type = "LRS"

  tags = {
    environment = "demo"
  }
}


# variables.tf
variable "aws_region" {
  description = "The AWS region where resources will be deployed."
  type        = string
  default     = "centralindia"
}

variable "project_name" {
  description = "The name of the project, used for naming and tagging."
  type        = string
  default     = "tiang-terraform"
}



https://github.com/user-attachments/assets/2f12d48b-0ebc-444d-a322-a597db043f42
https://github.com/user-attachments/assets/9afe29e0-840a-4d61-8a45-3255d9e51c8d
https://github.com/user-attachments/assets/7039bdaa-6bd7-452e-adac-a49997f84eae




