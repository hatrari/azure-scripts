# Geo replication for Azure Container Registry

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Create an ACR
`az acr create --location eastasia --resource-group myResourceGroup --name myContainerRegistryGeoRep --sku Premium`

> Resource group must be premium

## Create a replication
`az acr replication create --location eastus --registry myContainerRegistryGeoRep`

## List all of the regions for a geo-replicated ACR
`az acr replication list --registry myContainerRegistryGeoRep -o table`

## Delete a replica
`az acr replication delete --name eastus --registry myContainerRegistryGeoRep`