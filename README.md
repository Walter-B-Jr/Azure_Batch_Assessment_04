## Lab Name: AzureBatch.L200.Troubleshooting.4

### Introduction
This is a Level 200 lab for Troubleshooting in Azure Batch. It is a **self-contained failure scenario**: deploying the template stands up the entire environment *and* runs the failing workload automatically. There is **no console app to build or run** and **no manual steps** — your job is purely to diagnose the failure with our internal tools.

## Deployment Instructions

Deploy the ARM template **`azuredeploy.json`** (root of this repo) using any option below.

### Option 1 - Deploy to Azure (one-click)
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FWalter-B-Jr%2FAzure_Batch_Assessment_04%2Fmaster%2Fazuredeploy.json)

Click the button, pick (or create) a resource group + region, optionally set `namePrefix`, then **Review + create** -> **Create**.

### Option 2 - Azure CLI
```powershell
az group create -n rg-batch-lab-04 -l eastus2
az deployment group create -g rg-batch-lab-04 --template-file azuredeploy.json --parameters namePrefix=batlab04
```
> Pick a region where your subscription has Batch **dedicated core quota** so the pool node can allocate.

### Option 3 - Azure Portal (Load file)
1. Portal -> search **Deploy a custom template** -> **Build your own template in the editor**.
2. **Load file** -> select `azuredeploy.json` -> **Save**.
3. Choose/create a resource group + region, optionally set `namePrefix`, then **Review + create** -> **Create**.

## What happens automatically
The deployment creates the Batch and Storage accounts, a compute pool, and (via a short-lived seed container) a job that **uses task dependencies** and is configured to **terminate when all tasks complete**. The pool node boots and runs the tasks. Allow several minutes after deployment before investigating the job/task state.

## Resources Created
- A Resource Group
- A Batch Account
- A Storage Account
- A Batch **Pool** (`batch_assessment_04_pool`)
- A Batch **Job** (uses task dependencies, terminate-on-completion) + **Tasks** (`batch_assessment_04_job`)
- A short-lived User-Assigned Managed Identity + Container Instance used only to seed the job/tasks

## Scenario
1. After the job runs, it is supposed to take only ~5 minutes to complete after being scheduled, according to the customer (Note: this is specific to this scenario; a Job takes however long is necessary to run the customer's Tasks or reach the configured timeout). After running, the Job is still in an **Active** state. The customer has set the Job to terminate after completion.
2. You are required to identify why the Job failed to terminate. Remember, the customer has configured the Job to terminate after completion.
3. The engineer should take a screenshot of how they identified the error (using Kusto and Azure Batch Diagnostics) and explain the reason why the Job failed to complete/terminate.

## Your Goal
Your goal is to identify why the Job is remaining in the **active** state (Kusto & Azure Batch Diagnostics). Take a snapshot of the two tools once you find the indication of error. Also, explain why the Job never terminates.

## Proof of Solution
1. Provide a screen capture of Kusto once you have found the error, highlighting the relevant indicators of why the Job is still in an **Active** state.
2. Provide a screen capture of the Azure Batch Diagnostics tool once you have found the error. Again, highlight the relevant indicators.
3. Bonus: Explain why the Job failed to terminate and is still **Active** after 5 minutes (when the Job should have completed).

## Important: After completing the lab
Please make sure to delete all the resources you created for this lab.
