# Running Batch jobs with Azure CLI

## Create a new resource group
`az group create --location eastasia --name myResourceGroup`

## Create a Batch account
`az batch account create --location eastasia --resource-group myResourceGroup --name mybatch`

## Log in to a Batch account
`az batch account login --resource-group myResourceGroup --name mybatch`

## Create a Batch pool in an account
`az batch pool create --id mypool --vm-size Standard_A1 --image canonical:ubuntuserver:16.04-LTS --node-agent-sku-id "batch.node.ubuntu 16.04"`

## Resize the pool to start some VMs
`az batch pool resize --pool-id mypool --target-dedicated 2`

> After a few minutes, the state of the pool is Steady, and the nodes start.

## List the compute nodes running in a pool
`az batch node list --pool-id mypool`

## Lists all of the Pools in the specified Account
`az batch pool list --account-name mybatch`

## Add a job to a Batch account
`az batch job create --pool-id mypool --id myjob`

## List all of the jobs or job schedule in a Batch account
`az batch job list --account-name mybatch`

## Create Batch tasks
`az batch task create --job-id myjob --task-id mytask --command-line "/bin/bash -c 'printenv | grep AZ_BATCH; sleep 90s'"`

## Lists all of the Tasks that are associated with the specified Job
`az batch task list --job-id myjob`

## View task status
`az batch task show --job-id myjob --task-id mytask`

## View task output
`az batch task file list --job-id myjob --task-id mytask --output table`

## Download one of the output files to a local directory
`az batch task file download --job-id myjob --task-id mytask --file-path stdout.txt --destination ./stdout.txt`

## Clean up resources
`az batch pool delete --pool-id mypool`