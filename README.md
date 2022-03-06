# microsoft-azure-trial-hackathon-dev-to

This application repository has been created to host the application code for the application developed in response to the Microsoft Azure Trial Hackathon on Dev .
You can find more details about the hackathon at - https://dev.to/devteam/hack-the-microsoft-azure-trial-on-dev-2ne5

There are many categories to select for in which you can deploy/choose your application.
They are -
1. AI Aces: Use Azure Artificial Intelligence & Machine Learning services (ex: Azure Bot Service, Cognitive Search, Computer Vision, Custom Vision, LUIS, ML, etc) to build a new application.
2. Computing Captains: Use Azure Compute Services (ex: Azure Functions, App Service, AKS, etc) to build a new application.
3. Low-Code Legends: Use Azure low code/no code Fusion development services (with the Power Apps trial add-on) to build a new application.
4. Java Jackpot: Use Azure's Java services to build a new Java app.
5. Wacky Wildcards: Create a silly, weird, and/or totally random application using Microsoft Azure's services that doesn’t fit into any of the categories above.

For my case , I have selected the category 2 - Computing Captains.

My application is a very simply voting application that is hosted on Azure Kubernetes Service .
The front end is created using HTML , and the tech stack is python .
It is inspired by the AKS tutorial published by MS as Open-Source , located at - https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-prepare-app

The application is a simple voting application that can let any user choose what is his favorite Public Cloud provider .
The application is hosted on AKS , and is accessible at - http://20.62.221.90/

The application looks like - 

<img width="702" alt="Capture" src="https://user-images.githubusercontent.com/6042946/156921275-efcd8d2f-9e35-4c22-b87f-e314934af6c0.PNG">

Related dev.to blog article can be found at - https://dev.to/turjachaudhuri/azure-trial-hackathon-submission-favorite-public-cloud-provider-voting-app-ilj

The code can be found in this repo , but the commands to create the Azure infrastrucutre to support the code is listed below ->

az acr create --resource-group hackathon-dev-to --name hackathondevto --sku Basic
az acr login --name hackathondevto
az acr list --resource-group hackathon-dev-to --query "[].{acrLoginServer:loginServer}" --output table => hackathondevto.azurecr.io
docker tag mcr.microsoft.com/azuredocs/azure-vote-front:v1 hackathondevto.azurecr.io/azure-vote-front:v1
docker push hackathondevto.azurecr.io/azure-vote-front:v1

az aks create --resource-group hackathon-dev-to --name hackathondevto --node-count 2 --generate-ssh-keys --attach-acr '/subscriptions/d0aae499-f910-4d0c-a3e7-2986a6f02c82/resourceGroups/hackathon-dev-to/providers/Microsoft.ContainerRegistry/registries/hackathondevto'

az aks get-credentials --resource-group hackathon-dev-to --name hackathondevto


