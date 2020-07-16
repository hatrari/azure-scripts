# Creating and Deleting a Resource Group

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## List resource groups
`az group list`

## Gets a resource group
`az group show --name myResourceGroup`
```
  {
    "id": "ID",
    "location": "....",
    "managedBy": null, 
    "name": "myResourceGroup",
    "properties": {
      "provisioningState": "Succeeded"
    },
    "tags": null,
    "type": "Microsoft.Resources/resourceGroups"
  }
```

`az group show --name myResourceGroup --query 'id'`
```
"ID"
```

## Delete a resource group
`az group delete --name myResourceGroup --yes --no-wait`