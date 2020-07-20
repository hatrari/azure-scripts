# Deploy an Azure Kubernetes Service (AKS) cluster

## Create a resource group
`az group create --location eastus --name myAKSCluster`

## Create AKS cluster
`az aks create --resource-group myAKSCluster --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys`

## Install Kubernetes command-line client (kubectl)
`az aks install-cli`

## Configure kubectl to connect to your Kubernetes cluster
`az aks get-credentials --resource-group myAKSCluster --name myAKSCluster`

## Verify the connection to your cluster
`kubectl get nodes`

> Output: <br>
> NAME                          STATUS  ROLES   AGE   VERSION <br>
> k8s-myAKSCluster-36346190-0   Ready   agent   2m    v1.7.7

## Run the application
> A Kubernetes manifest file (.yaml) defines a desired state for the cluster, including what container images should be running.

`kubectl apply -f azure-vote.yaml`

> Output : <br>
> deployment "azure-vote-back" created <br>
> service "azure-vote-back" created <br>
> deployment "azure-vote-front" created <br>
> service "azure-vote-front" created

## Test the application
> To monitor progress, use the kubectl get service command with the --watch argument

`kubectl get service azure-vote-front --watch`

> Once the EXTERNAL-IP address has changed from pending to an IP address, use CTRL-C to stop the kubectl watch process. <br>
> Now browse to the external IP address to see the Azure Vote App.

## Delete cluster
`az aks delete --resource-group myAKSCluster --name myAKSCluster`