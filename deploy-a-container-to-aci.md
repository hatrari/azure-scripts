# Deploy a container to Azure Container Instances (ACI)

> In this section, you use the Azure CLI to deploy the image you have already built and pushed to Azure Container Registry.

## Get the full name of the container registry login serve
`az acr show --name mycontainerregistry --query loginServer`

> acrLoginServer

## Enable admin to get the container registry password
`az acr update --name mycontainerregistry --admin-enabled true`

## Get the container registry password
`az acr credential show --name mycontainerregistry --query "passwords[0].value"`

> acrPassword

## Deploy the container
`az container create --resource-group myResourceGroup --name aci-tutorial-app --image <acrLoginServer>/aci-tutorial-app:v1 --cpu 1 --memory 1 --registry-login-server <acrLoginServer> --registry-username <acrName> --registry-password <acrPassword> --dns-name-label <aciDnsLabel> --ports 80`

> The --dns-name-label value must be unique within the Azure region you create the container instance. Modify the value in the preceding command if you receive a DNS name label error message when you execute the command.

## Verify deployment progress
`az container show --resource-group myResourceGroup --name aci-tutorial-app --query instanceView.state`

> Repeat the az container show command until the state changes from Pending to Running, which should take under a minute.

## Display the container's fully qualified domain name (FQDN)
`az container show --resource-group myResourceGroup --name aci-tutorial-app --query ipAddress.fqdn`

## View the log output of the container
`az container logs --resource-group myResourceGroup --name aci-tutorial-app`