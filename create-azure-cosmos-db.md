# Creates an Azure Cosmos DB database

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Creates a new Azure Cosmos DB database account
`az cosmosdb create --resource-group myResourceGroup --name myAccount`

## List the connection strings for a Azure Cosmos DB database account
`az cosmosdb keys list --resource-group myResourceGroup --name myAccount --type connection-strings`

## Creates an Azure Cosmos DB database
`az cosmosdb sql database create --resource-group myResourceGroup --account-name myAccount --name myDatabase`

> cosmosdb __sql__ database

> cosmosdb __mongodb__ database

> cosmosdb __cassandra__ keyspace

> cosmosdb __gremlin__ database

## Create an SQL container under an Azure Cosmos DB SQL database
`az cosmosdb sql container create --resource-group myResourceGroup --account-name myAccount --database-name myDatabase --name myContainer --partition-key-path '/tetspartition'`

> cosmosdb sql __container__

> cosmosdb mongodb __collection__

> cosmosdb cassandra __table__

> cosmosdb gremlin __graph__

## List the SQL containers under an Azure Cosmos DB SQL database
`az cosmosdb sql database list --resource-group myResourceGroup --account-name myAccount`