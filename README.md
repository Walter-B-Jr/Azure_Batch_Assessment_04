## Lab Name: AzureBatch.L200.JobTroubleshooting.4

## Introduction
This is a Level 200 lab for the Troubleshooting in Azure Batch.
## Deployment Instructions
1.	Deploy the template and download the source code.
2.	Open up the application that was created in the deployment template to get the credentials required for the sample code to work correctly. Then, proceed to open the code sample in VS and make the following required changes:
a.	Open “Program.cs” under DotNetTutorial application. 
b.	Proceed to enter the credentials provided in the application to the code sample as shown below
i.	BatchAccountName
ii.	BatchAccountKey
iii.	BatchAccountUrl
iv.	StorageAccountName
v.	StorageAccountKey
vi.	You can name your PoolID and JobID however you desire.

## Resources Created
This lab involves the following resources.
-	Resource Group
-	Batch Account 
-	Storage Account 
-	Application – (which contains Batch and Storage credentials
## Scenario
1.	After running the job, the job is supposed to take only ~5 minutes to run after being scheduled, according to the customer (Note: this is specifically for this scenario. A Job will take however long it is necessary to run the customers Tasks code or reach the timeout specified by customer…). After running, the Job is still in Active State. The customer has set the Job to terminate after completion. 
2.	You are required to identify why the Job failed to terminate. Remember, the customer has configured the Job to terminate after completion.
3.	The engineer should take a screenshot of how they identified the error (using Kusto and Azure Batch Diagnostics) and explain the reason why the Job failed to complete/terminate.
 
## Your Goal
Your goal is to identify why the Job is remaining in “active” state (Kusto & Azure Batch diagnostics). Take a snapshot of the two tools (Kusto & Azure Batch diagnostics) once you find the indication of error. Also, explain why the Job never terminates. 
## Proof of Solution
1.	Provide a screen capture of KUSTO once you have found the error, highlighting the relevant indicators of why the Job might still be in an “Active” state.
2.	Provide a screen capture of the AzureBatchDiagnostics once you have found the error. Again, highlight the relevant indicators of why the Job might still be in an “Active” state.
3.	Bonus: Explain why the Job failed to terminate and is still in “Active” state after 5 minutes (when the Job should have completed).
