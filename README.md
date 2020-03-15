This ARM template can be used to create a Azure Alert for any Virtual Machine in Azure Cloud. Note that this is applicable for a single virtual machine.

You can execute this ARM template project in two ways.

Procedure 1: Executing from Visual Studio.

 Step 1: Clone this solution to your local machine and open the solution using Visual Studio 2019 or 2017. Created this project using Visual Studio 2019.
 
 Step 2: Right Click on the Project from Solution Explorer. Click on Deploy option
 Step 3: Provide your Valid Azure Subscription name and Deployment Group. Update the values in the file azurealerts.parameters.json. You can do so by clicking on the button "Edit Parameters"
 Step 4: Now Click on Deploy button.
 
 That's it. It takes a couple of minutes for your template to create Azure Alert in Azure Cloud.
 Login to Azure portal and check the newly created Azure Alert.
 
 Name of the Alert that I have provided in the file azurealerts.parameters.json is "PurnaDemoAlertCPUforVM"
 
 
 Procedure 2: Execute from Powershell window
 
 Update the Value tags in the json file azurealerts.parameters.json as per your valid resource details. I have provided my details for the reference.
 
 
 Step 1: Open Powershell ISE or PowerShell command prompt.
 Step 2: Use the below commands in the same order.
 
 Step 2.1 Connect-AzAccount  
 
 Note: This command will open up a pop-up and you need to provide valid azure credentials

Step 2.2 Select-AzSubscription -SubscriptionName "Azure subscription 1"  
  Note : Replace "Azure Subscription 1" with the name of your valid subscription
 
Step 2.3 

In the below command - replace the file paths as per the paths of your azurelerts.json and azurealerts.parameters.json files

New-AzResourceGroupDeployment -Name PurnaAlertDeployment -ResourceGroupName DemoGroup `
  -TemplateFile C:\Users\Purnachandra.K\source\repos\ARMAlerts\ARMAlerts\azurealerts.json -TemplateParameterFile C:\Users\Purnachandra.K\source\repos\ARMAlerts\ARMAlerts\azurealerts.parameters.json
  
  Note:
  Below updtate subscription id which is after Subscriptions and resource group (DemoGroup) which is after resourcegroups
  Also, under ActionId tag updat subscription ID and resource Group ID which are same as the resourceId tag values.
  
  "resourceId": {
      "value": "/subscriptions/a9b9ec1f-xxxx-49b8-b3sdfb-3b368695b78b/resourceGroups/DemoGroup/providers/Microsoft.Compute/virtualMachines/DemoWebServer"
    },
    "metricName": {
      "value": "Percentage CPU"
    },
    "operator": {
      "value": "GreaterThan"
    },
    "threshold": {
      "value": "40"
    },
    "timeAggregation": {
      "value": "Average"
    },
    "actionGroupId": {
      "value": "/subscriptions/a9b9ec1f-xxxx-49b8-b3sdfb-3b368695b78b/resourceGroups/DemoGroup/providers/Microsoft.Insights/actionGroups/purnactiongroup"
    }
    
