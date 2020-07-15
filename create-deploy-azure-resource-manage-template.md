# Create and deploy Azure Resource Manage (ARM) templates

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Create a storage account
`az storage account create --location westus --resource-group MyResourceGroup --name mystorageaccount --sku Standard_LRS`

## Export resource group to a template
`az group export --name MyResourceGroup > template.json`

## Delete the storage account
`az storage account delete --resource-group myResourceGroup --name mystorageaccount --yes --no-wait`

## Start a deployment at resource group
`az deployment group create --resource-group myResourceGroup --template-file template.json`
