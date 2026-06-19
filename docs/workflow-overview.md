# Workflow Overview

## Automation Name

Automated Export Account Transactions from Xero to Asana

## Objective

Automatically export Xero account transaction data into a CSV-formatted file and upload the file to the related Asana task.

## High-Level Flow

```text
Completed Asana Task
        ↓
Retrieve Xero Account Transactions
        ↓
Format Transaction Rows
        ↓
Store Rows Temporarily in Google Sheets
        ↓
Generate CSV Output
        ↓
Upload CSV to Asana Task
        ↓
Clear Temporary Sheet Data
```

## Detailed Workflow Logic

### 1. Asana Trigger

The workflow begins when a task is marked complete in Asana. This task acts as the request or control record for the export.

### 2. Xero API Request

Make.com sends an API request to Xero to retrieve account transaction data. The request may include date ranges, account IDs, tracking categories, or other filters depending on the final configuration.

### 3. Router

The router splits the workflow into two paths:

- **Route 1:** Processes each transaction and writes rows into Google Sheets.
- **Route 2:** Waits briefly, retrieves the completed range, generates the CSV, uploads it to Asana, and clears the sheet.

### 4. Iterator

The iterator loops through transaction records returned by Xero so each transaction can be handled as an individual row.

### 5. Google Sheets Row Creation

Each transaction is written to a Google Sheet that acts as a temporary staging table.

### 6. CSV Generation

After the rows are written, the workflow retrieves the populated range and uses a text aggregator to convert the rows into a CSV-ready text file.

### 7. Upload to Asana

The generated CSV file is uploaded back to the Asana task as an attachment.

### 8. Cleanup

The Google Sheets range is cleared so the staging sheet is ready for the next export.

## Expected Output

A CSV file attached to the completed Asana task containing account transaction data exported from Xero.

## Make.com Shared Scenario

Public shared scenario link:

https://us2.make.com/public/shared-scenario/3niw9ogCiHQ/integration-asana-xero
