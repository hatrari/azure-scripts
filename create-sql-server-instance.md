# Create a new SQL Server Instance

## Create a server
`az sql server create --location westus --resource-group mygroup --name myserver --admin-user myadminuser --admin-password P@ssw0rd`

## Create a database
`az sql db create --resource-group mygroup --server myserver --name mydb`

## Generate connection string for ado\.net
`az sql db show-connection-string --server myserver --name mydb --client ado.net`