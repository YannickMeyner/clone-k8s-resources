# k8s-resources

These are the resource files for the chatbots and connecting worlds.

## Usage Azure

You need to install the Azure CLI on top of the kubectl cli. 

`az login` to log into the azure account.

`az aks get-credentials --resource-group fs25-group13 --name fs25-group13` to get the credentials for our cluster. If you have access to it.

## Secrets

First you need create the docker-registry secrets:
`kubectl create secret docker-registry acr-auth --docker-server=fs25group13.azurecr.io --docker-username=<username> --docker-password=<password> --namespace=k8s-resources`

These are used to pull the images from ACR.

Then you need to create a secret with the chatbot api keys:
`kubectl create secret generic chatbot-api-keys --from-literal=dotnet-chatbot-api-key=<HF_key> --from-literal=fastify-chatbot-api-key=<Grok-key> --namespace=k8s-resources`

## Applying

Then you can apply all files in order. 
- Configmaps
- Deployments
- Services

