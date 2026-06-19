# Setup Guide

## Prerequisites

Before building the scenario, make sure you have:

- A Make.com account
- Xero connection authorized in Make
- Asana connection authorized in Make
- Google Sheets connection authorized in Make
- A Google Sheet prepared as a temporary CSV staging sheet
- An Asana project where export request tasks are completed

## Step 1: Create the Asana Trigger

1. Add the **Asana > Watch Completed Tasks** module.
2. Connect the correct Asana workspace.
3. Select the project where export tasks are tracked.
4. Set the trigger to watch newly completed tasks.

## Step 2: Add the Xero API Call

1. Add **Xero > Make an API Call**.
2. Select the authorized Xero organization.
3. Configure the endpoint for account transactions.
4. Add any required query parameters such as account, date range, or status.

Example endpoint placeholder:

```text
/api.xro/2.0/BankTransactions
```

Adjust the endpoint based on the exact Xero transaction object being exported.

## Step 3: Add a Router

Add a Make.com router after the Xero module.

Create two routes:

- Route 1: Transaction row writing
- Route 2: CSV generation and Asana upload

## Step 4: Build Route 1

Route 1 should include:

1. **Iterator** to loop through Xero transaction records.
2. **Google Sheets > Add a Row** to write transaction fields into the staging sheet.

## Step 5: Build Route 2

Route 2 should include:

1. **Tools > Sleep** to allow Route 1 enough time to finish writing rows.
2. **Google Sheets > Get Range Values** to retrieve the staged CSV rows.
3. **Tools > Text Aggregator** to format the rows as CSV text.
4. **Asana > Upload an Attachment** to attach the CSV file to the task.
5. **Google Sheets > Clear Values from Range** to reset the staging sheet.

## Step 6: Test the Scenario

Run the scenario manually with a test Asana task and confirm:

- Xero returns transaction data.
- Google Sheets rows are created correctly.
- The CSV file is attached to the correct Asana task.
- The staging sheet is cleared after upload.

## Step 7: Activate the Scenario

Once testing is complete, turn the scenario on in Make.com.

## Shared Scenario Link

Use the shared Make.com scenario below as the starting point for setup or duplication:

https://us2.make.com/public/shared-scenario/3niw9ogCiHQ/integration-asana-xero

After importing, reconnect your own Asana, Xero, and Google Sheets accounts before running the scenario.
