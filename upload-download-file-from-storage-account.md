# Upload and download a file from a storage account

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Create a new storage account
`az storage account create --location eastasia --resource-group myResourceGroup --name mystorageaccount --sku Standard_LRS`

## List the access keys for a storage account
`az storage account keys list --resource-group myResourceGroup --account-name mystorageaccount`

## Creates a new share under the specified account
`az storage share create --account-name mystorageaccount --account-key <key> --name myfileshare`

## Upload a file
`az storage file upload --account-name mystorageaccount --account-key <key> --share-name myfileshare --source file.txt`

## List files and directories in a share
`az storage file list --account-name mystorageaccount --account-key <key> --share-name myfileshare`

## Generates a shared access signature (SAS) for the file
`az storage file generate-sas --account-name mystorageaccount --share-name myfileshare --account-key <key> --path file.txt --permissions rcdw --expiry 2037-12-31T23:59:00Z`

## Create the url to access a file
`az storage file url --account-name mystogeacco --share-name myfileshare --account-key <key> --path file.txt`