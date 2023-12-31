Pareto Anywhere Quickstart - POC
=========================

Getting Started
---------------

This is a quickstart template that users can use to deploy __Pareto Anywhere for Azure__.
It is an automated solution to walk through the step-by-step tutorial found [here](https://reelyactive.github.io/diy/pareto-anywhere-azure/).

The templates and workflows provided will create the following resources: 
* IoT Hub
* Device Provisioning Service
* Event Hubs Namespace
* Event Hub
* Shared Access Policy
* Web PubSub
* Storage Account
* Function App 

After the supporting infrastructure is created, the template will also deploy the __Pareto Anywhere for Azure__ application code to the function app with the required settings and configuration.

To use this solution, you will need the following:
- An Azure account
- An Azure Subscription
- An Azure Resource Group


### Step 1: Configure IoT Hub and Device Provisioing Service
When you are ready to configure the IoT Hub Service and DPS, deploy to Azure with to the button below:

[![Deploy IoT Hub and DPS](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fadeany%2Fquickstart-pareto%2Fmain%2Fdeployments%2Fdevice_template.json)

### Step 2: Add Enrollment Group
After the IoT Hub and DPS are configured, you can add the enrollment group by kicking off the [Add Enrollment Group Github Action Workflow](https://github.com/adeany/quickstart-pareto/actions/workflows/add-enrollment-group.yml).

Notes:
* This workflow requires the following Github Action Repsoitory secrets to be configured: `CLUSTER_SERVICE_PRINCIPAL` (JSON object for your service principal), `SUBSCRIPTION_ID` and `RESOURCE_GROUP`. More information on how to add these repository secrets is [documented here](https://learn.microsoft.com/en-us/azure/developer/github/connect-from-azure?tabs=azure-portal%2Cwindows).
* Make sure your inputs match the names of the DPS and IoT Hub resources that you specified in the IoT Hub and DPS deployment above
* You can find the Aruba client side connection configuration variables in the `Print Device Connection data` step of the workflow run

### Step 3: Deploy Pareto Anywhere to Azure
When you are ready to spin up Pareto Anywhere and the supporting resources, deploy to Azure with to the button below:

[![Deploy Pareto Anywhere to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fadeany%2Fquickstart-pareto%2Fmain%2Fdeployments%2Fsupporting_resources_template.json)

After deployment is complete, you may browse to the web app on Azure by pointing a web browser to __https://app-name.azurewebsites.net/app/__, substituting app-name for the Function name you specified in the template.

Developer Notes
---------------

This template uses a zip file to deploy the Pareto Anywhere application code to Azure
* The file is located in this repository and named `pareto-anywhere.zip`
* The template references this zip using a variable named `functionPackageUri`. If you wish to change the location of the zip file containing the Pareto Anywhere application code, you must update this uri in the [ARM template](./deployments/supporting_resources_template.json).

License
-------

MIT License

Copyright (c) 2022-2023 [reelyActive](https://www.reelyactive.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR 
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, 
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE 
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER 
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, 
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN 
THE SOFTWARE.
