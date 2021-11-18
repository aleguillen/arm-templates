# Create a logic app to start/stop resource group VMs by using a template

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faleguillen%2Farm-templates%2Fmain%2Frecurrent-start-stop-vms%2Fazuredeploy.json)
[![Deploy To Azure US Gov](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazuregov.svg?sanitize=true)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faleguillen%2Farm-templates%2Fmain%2Frecurrent-start-stop-vms%2Fazuredeploy.json)
[![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Faleguillen%2Farm-templates%2Fmain%2Frecurrent-start-stop-vms%2Fazuredeploy.json)

Azure Logic Apps is a cloud service that automates the execution of your business processes. You use a graphical design tool called the Logic Apps Designer to arrange pre-made components into the sequence you need. The Designer sends a definition of your workflow to the Logic Apps execution engine. The execution engine launches your app when conditions are right and manages the compute resources needed to run it.

This simple logic app manages your Resource Group VMs and VMSSs schedule to Start in the morning and Stop in the evening during weekdays to save cost where is provisioned.

ARM Template parameters:

| Parameter Name | Description | Default Value | 
| --- | --- | --- |
| logicAppName | The name of the logic app to create. | recurrent-start-stop-vms-la |
| location | The name of the logic app to create. Default to current Resource Group's location. | [resourceGroup().location] |
| startTime | Specify exact hour of the morning to start VMs. E.g. is set to 7 it will start VMs at 7 AM. | 7 |
| stopTime | Specify exact hour of the evening to stop VMs. E.g. is set to 19 it will stop VMs at 7 PM. | 19 |
| atMinute | Specify exact minute of the Hour to start/stop VMs. Defaults to 0. E.g. If set to 30 it will start at 7:30 and stop at 19:30 each weekday. | 0 |
| timeZone | Time Zone for your Logic App recurrent trigger. | Central Standard Time |
| morningAction | Specify the default action for morning. Defaults to Start. E.g. if set to Deallocate it will stop the VMs during AM hours and start during PM hours. | start |
| runOn | Specify the days to run. Weekdays: Mon-Fri, Weekend: Sat-Sun, Week: Mon-Sun. | Weekdays |
| includeVMSS | Specify wether to include VMSS in the start/stop operation. | false |
| excludedResources | Specify a comma-separated list of VMs or VMSSs to exclude from the resource group. Ex. VM1,VM2,VMSS1 |  |


For information about using this template, see [Create Azure Resource Manager templates for Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-create-deploy-template). To learn more about how to deploy the template, see the [quickstart](https://docs.microsoft.com/azure/logic-apps/quickstart-create-deploy-azure-resource-manager-template) article.

- [Microsoft Logic Apps](https://azure.microsoft.com/services/logic-apps/)
- [Microsoft Logic Apps Documentation](https://docs.microsoft.com/azure/logic-apps/)
- [Microsoft Learn Logic App Modules](https://docs.microsoft.com/learn/browse/?term=logic%20app)