```terraform
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
    }
  }
}

provider "azurerm" {
  features {}
  subscription_id = "f1a145f5-f75d-4170-a316-576364d2886b"
}

resource "azurerm_resource_group" "example" {
  name     = "Example1"
  location = "eastus"
}
```