# Sign in to Azure
az login

# Create and set the default resource group
az group create --name <resource-group-name> --location <location>

# Deploy ARM template
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="blanktemplate-"$today

az deployment group create --name $DeploymentName --template-file $templateFile

# Deploy the updated ARM template
<!--Here, we change the name of the deployment to better reflect what this deployment does.-->
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addstorage-"$today

az deployment group create --name $DeploymentName --template-file $templateFile

# Deploy the ARM template with a value for the parameter (storageName)
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addnameparameter-"$today

az deployment group create --name $DeploymentName --template-file $templateFile --parameters storageName={your-unique-name}

# Deploy the ARM template with a value for the parameter (storageSKU)
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addSkuParameter-"$today

az deployment group create --name $DeploymentName --template-file $templateFile --parameters storageSKU=Standard_GRS storageName={your-unique-name}

# Deploy the ARM template with an output (storageEndpoint)
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addoutputs-"$today

az deployment group create --name $DeploymentName --template-file $templateFile --parameters storageSKU=Standard_LRS storageName={your-unique-name}

