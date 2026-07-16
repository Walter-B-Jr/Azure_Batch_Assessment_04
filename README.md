## Lab Name: AzureBatch.L200.JobTroubleshooting.4

## Introduction
This is a Level 200 lab for the Troubleshooting in Azure Batch.
## Deployment Instructions

Deploy the ARM template **`azuredeploy.json`** (in the root of this repo) using **either** option below.

### Option 1 - Azure CLI (recommended)
```powershell
az group create -n rg-batch-lab-04 -l westus2
az deployment group create -g rg-batch-lab-04 --template-file azuredeploy.json --parameters namePrefix=batlab04
az deployment group show -g rg-batch-lab-04 -n azuredeploy --query properties.outputs
```

### Option 2 - Azure Portal (Load file)
1. Portal -> search **Deploy a custom template** -> **Build your own template in the editor**.
2. **Load file** -> select `azuredeploy.json` from this repo -> **Save**.
3. Choose/create a resource group + region, set `namePrefix`, then **Review + create** -> **Create**.

### Option 3 - Deploy to Azure button
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2FWalter-B-Jr%2FAzure_Batch_Assessment_04%40master%2Fazuredeploy.json)

> Note: the one-click button fetches the template from a public CDN. Some corporate networks block that outbound fetch (the portal then shows a generic "enable CORS" error) - use Option 1 or 2 instead.

### After deploying
Open the deployment **Outputs** for `batchAccountName`, `batchAccountUrl`, and `storageAccountName`, then get the keys from the portal:
- Batch account -> **Keys** -> account **URL** + **Primary access key**.
- Storage account -> **Access keys** -> account name + **key1**.

Paste these into `DotNetTutorial\Program.cs` (`BatchAccountName`, `BatchAccountUrl`, `BatchAccountKey`, `StorageAccountName`, `StorageAccountKey`), then build and run the console app.

<details><summary>Manual deployment (alternative)</summary>
1.	Deploy the template and download the source code. https://github.com/Walter-B-Jr/Azure_Batch_Assessment_04
2.	Open up the application that was created in the deployment template to get the credentials required for the sample code to work correctly. Then, proceed to open the code sample in VS and make the following required changes:
a.	Open �Program.cs� under DotNetTutorial application. 
b.	Proceed to enter the credentials provided in the application to the code sample as shown below
i.	BatchAccountName
ii.	BatchAccountKey
iii.	BatchAccountUrl
iv.	StorageAccountName
v.	StorageAccountKey
vi.	You can name your PoolID and JobID however you desire.

</details>

## Resources Created
This lab involves the following resources.
-	Resource Group
-	Batch Account 
-	Storage Account 
## Scenario
1.	After running the job, the job is supposed to take only ~5 minutes to run after being scheduled, according to the customer (Note: this is specifically for this scenario. A Job will take however long it is necessary to run the customers Tasks code or reach the timeout specified by customer�). After running, the Job is still in Active State. The customer has set the Job to terminate after completion. 
2.	You are required to identify why the Job failed to terminate. Remember, the customer has configured the Job to terminate after completion.
3.	The engineer should take a screenshot of how they identified the error (using Kusto and Azure Batch Diagnostics) and explain the reason why the Job failed to complete/terminate.
 
## Your Goal
Your goal is to identify why the Job is remaining in �active� state (Kusto & Azure Batch diagnostics). Take a snapshot of the two tools (Kusto & Azure Batch diagnostics) once you find the indication of error. Also, explain why the Job never terminates. 
## Proof of Solution
1.	Provide a screen capture of KUSTO once you have found the error, highlighting the relevant indicators of why the Job might still be in an �Active� state.
2.	Provide a screen capture of the AzureBatchDiagnostics once you have found the error. Again, highlight the relevant indicators of why the Job might still be in an �Active� state.
3.	Bonus: Explain why the Job failed to terminate and is still in �Active� state after 5 minutes (when the Job should have completed).
