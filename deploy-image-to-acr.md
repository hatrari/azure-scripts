# Deploy an image to Azure Container Registrie (ACR)

> Docker must __be running__ before you can do anything.

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Create an Azure Container Registry
`az acr create --resource-group myResourceGroup --name mycontainerregistry --sku Basic`

## Log in to an Azure Container Registry through the Docker CLI
`az acr login --name mycontainerregistry`

## Push image to registry

### Pull the hello-world image
`docker pull hello-world`

### Tag the image
`docker tag hello-world mycontainerregistry.azurecr.io/hello-world:v1`

### Push the image to the ACR instance
`docker push mycontainerregistry.azurecr.io/hello-world:v1`

## List container services
`az acr repository list --name mycontainerregistry --output table`