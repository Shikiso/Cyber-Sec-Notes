# Azure Resource Manager
You can use Azure Resource Manager templates (ARM templates) to implement infrastructure as code.

Infrastructure code allows you to describe, through code, the infrastructure that you need for your application. 

## ARM Templates
ARM templates are JSON files that define the infrastructure and configuration for your deployment. Allowing you to declare what you intend to deploy without having to write the sequence of programming commands to create it.

### File Structure
When you're writing an ARM template, you need to understand all the parts that make up the template and what they do. ARM template files are made up of the following elements:

| Element            | Description                                                                                                                                                                                                                                                                                                                              |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **schema**         | A required section that defines the location of the JSON schema file that describes the structure of JSON data. The version number you use depends on the scope of the deployment and your JSON editor.                                                                                                                                  |
| **contentVersion** | A required section that defines the version of your template (such as 1.0.0.0). You can use this value to document significant changes in your template to ensure you're deploying the right template.                                                                                                                                   |
| **apiProfile**     | An optional section that defines a collection of API versions for resource types. You can use this value to avoid having to specify API versions for each resource in the template.                                                                                                                                                      |
| **parameters**     | An optional section where you define values that are provided during deployment. You can provide these values in a parameter file, by command-line parameters, or in the Azure portal.                                                                                                                                                   |
| **variables**      | An optional section where you define values that are used to simplify template language expressions.                                                                                                                                                                                                                                     |
| **functions**      | An optional section where you can define [user-defined functions](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/template-user-defined-functions) that are available within the template. User-defined functions can simplify your template when complicated expressions are used repeatedly in your template. |
| **resources**      | A required section that defines the actual items you want to deploy or update in a resource group or a subscription.                                                                                                                                                                                                                     |
| **output**         | An optional section where you specify the values that are returned at the end of the deployment.                                                                                                                                                                                                                                         |
## Deploy ARM Template
You can deploy a ARM template in either of the following:
- Deploy a local template
- Deploy a linked template
- Deploy in a continuous deployment pipeline

To deploy a local template you need to have either Azure Powershell or Azure CLI installed locally.

| Step                  | CLI                                                                                                                                                                          | Powershell                                                                                                                                                                        |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Login                 | `az login`                                                                                                                                                                   | `Connect-AzAccount`                                                                                                                                                               |
| Define resource group | `az group create --name {name of your resource group} --location "{location}"`                                                                                               | `New-AzResourceGroup -Name {name of your resource group} -Location "{location}"`                                                                                                  |
| Deploy resource group | `templateFile="{provide-the-path-to-the-template-file}"`<br>`az deployment group create --name blanktemplate --resource-group myResourceGroup --template-file $templateFile` | `$templateFile = "{provide-the-path-to-the-template-file}"`<br>`New-AzResourceGroupDeployment -Name blanktemplate -ResourceGroupName myResourceGroup -TemplateFile $templateFile` |
The problem with this is that the name is hard coded meaning to deploy a template with a different name you will need to create a new template which isn't practical.

## ARM-Template Parameters
Let you customize the deployment by providing values that are tailored for a particular environment.

In the `parametes` section of the template you specify which values you can input when you deploy. The available properties for a parameter are:
```
"parameters": {
  "<parameter-name>": {
    "type": "<type-of-parameter-value>",
    "defaultValue": "<default-value-of-parameter>",
    "allowedValues": [
      "<array-of-allowed-values>"
    ],
    "minValue": <minimum-value-for-int>,
    "maxValue": <maximum-value-for-int>,
    "minLength": <minimum-length-for-string-or-array>,
    "maxLength": <maximum-length-for-string-or-array-parameters>,
    "metadata": {
      "description": "<description-of-the-parameter>"
    }
  }
}
```
The allowed types of parameters are:
- string
- secureString
- integers
- boolean
- object
- secureObject
- array

## Recommendations for using Parameters
- Use parameters for settings that vary according to the environment
- Use parameters for names you want to specify yourself
- Provide a description for each parameter

## Use Parameters in an ARM Template
In the parameters section of the ARM template specify the parameters that you can input when you deploy the resources.

Here is an example with a parameter for the storage-account SKU defines in the templates parameters section.
```
"parameters": {
  "storageAccountType": {
    "type": "string",
    "defaultValue": "Standard_LRS",
    "allowedValues": [
      "Standard_LRS",
      "Standard_GRS",
      "Standard_ZRS",
      "Premium_LRS"
    ],
    "metadata": {
      "description": "Storage Account type"
    }
  }
}
```

Next use the parameter in the resource definition.
```
"resources": [
  {
    "type": "Microsoft.Storage/storageAccounts",
    "apiVersion": "2025-01-01",
    "name": "learntemplatestorage123",
    "location": "[resourceGroup().location]",
    "sku": {
      "name": "[parameters('storageAccountType')]"
    },
    "kind": "StorageV2",
    "properties": {
      "supportsHttpsTrafficOnly": true
    }
  }
]
```

When you deploy the template you can provide a value for the parameter.

| CLI                                                                                                                                                                                                 | Powershell                                                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `templateFile="azuredeploy.json"`<br>`az deployment group create \`<br>`  --name testdeployment1 \`<br>`  --template-file $templateFile \`<br>`  --parameters`<br>`storageAccountType=Standard_LRS` | `$templateFile="azuredeploy.json"`<br>`New-AzResourceGroupDeployment`<br>`-Name testdeployment1`<br>`-TemplateFile $templateFile`<br>`-storageAccountTypeStandard_LRS` |
## ARM Template Outputs
In your ARM template's outputs section, you can specify the values that are returned after a successful deployment. Here are the elements that make up the outputs section.
```
"outputs": {
  "<output-name>": {
    "condition": "<boolean-value-whether-to-output-value>",
    "type": "<type-of-output-value>",
    "value": "<output-value-expression>",
    "copy": {
      "count": <number-of-iterations>,
      "input": <values-for-the-variable>
    }
  }
}
```

| Element         | Description                                                                                                                                                                                                                                                     |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **output-name** | Must be a valid JavaScript identifier.                                                                                                                                                                                                                          |
| **condition**   | (Optional) A Boolean value that indicates whether this output value is returned. When true, the value is included in the output for the deployment. When false, the output value is skipped for this deployment. When not specified, the default value is true. |
| **type**        | The type of the output value.                                                                                                                                                                                                                                   |
| **value**       | (Optional) A template language expression to be evaluated and returned as an output value.                                                                                                                                                                      |
| **copy**        | (Optional) Copy is used to return more than one value for an output.                                                                                                                                                                                            |
# Use outputs in an ARM Template
Example:
```
"outputs": {
  "storageEndpoint": {
    "type": "object",
    "value": "[reference('learntemplatestorage123').primaryEndpoints]"
  }
}
```
