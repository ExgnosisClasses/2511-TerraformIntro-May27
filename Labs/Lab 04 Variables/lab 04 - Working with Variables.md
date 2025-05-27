# Lab 4: Working with variables

For this lab, we will 


## Part 1: Deploy a resource

### Hardcoded

Just like you did in the previous labs
- Delete any previous `main.tf` file in your cloud shell
- Upload the `main1.tf` file from the lab 4 directory.
- Use the same `providers.tf` file from before

```terraform
## Lab 4 configuration - hard coded

resource "azurerm_resource_group" "lab4" {
  name     = "Lab4"
  location = "eastus"
  tags = {
      environment = "test environment"
      owner       = "The wonder lama"
      purpose     = "demonstrate stuff"
    }
}
```


- Just like you did before, use `terraform apply` to create the resource'

```console
 terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # azurerm_resource_group.lab3 will be created
  + resource "azurerm_resource_group" "lab4" {
      + id       = (known after apply)
      + location = "eastus"
      + name     = "Lab4"
      + tags     = {
          + "environment" = "test environment"
          + "owner"       = "Zippy"
          + "purpose"     = "demonstrate stuff"
        }
    }

Plan: 1 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

azurerm_resource_group.lab4: Creating...
azurerm_resource_group.lab4: Creation complete after 10s [id=/subscriptions/f1a1xxxxxxxxxxxxxxxxxxxxxxxxxxxxx86b/resourceGroups/Lab3]
```

## Part 2: Add a variables file

- Upload the file `variables.tf` from the lab folder
- The file looks like this

```terraform
variable "resource_group_name" {
  description = "The name of the resource group."
  type        = string
  default     = "Lab4"
}

variable "resource_group_location" {
  description = "The Azure region where the resource group will be created."
  type        = string
  default     = "eastus"
}
```

- Notice that default values have been procdied
`