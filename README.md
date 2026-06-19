# Automated Export Account Transactions from Xero to Asana

This Make.com workflow automates the export of account transaction data from Xero, formats the data as CSV-ready rows, uploads the CSV output to Asana, and logs processing details in Google Sheets.

## Workflow Summary

**Source:** Asana completed task trigger  
**Accounting System:** Xero  
**Processing Platform:** Make.com  
**Output:** CSV uploaded to Asana  
**Logging:** Google Sheets

## What This Automation Does

1. Watches for completed Asana tasks.
2. Calls the Xero API to retrieve account transaction data.
3. Routes the data based on processing requirements.
4. Iterates through transaction records.
5. Writes transaction rows into Google Sheets.
6. Retrieves the completed CSV data range.
7. Aggregates the rows into a CSV/text file format.
8. Uploads the generated CSV file back into Asana as an attachment.
9. Clears the temporary Google Sheets range after completion.

## Process Map

```text
Asana - Watch Completed Tasks
        ↓
Xero - Make API Call
        ↓
Router
   ├── Route 1: Iterate transaction rows → Google Sheets Add Row
   └── Route 2: Sleep → Google Sheets Get Range → Text Aggregator → Asana Upload Attachment → Google Sheets Clear Range
```

## Main Make.com Modules

| Step | App | Module | Purpose |
|---|---|---|---|
| 1 | Asana | Watch Completed Tasks | Starts the workflow when a task is completed |
| 2 | Xero | Make an API Call | Pulls account transaction data from Xero |
| 3 | Router | Router | Splits transaction-writing and CSV-upload paths |
| 4 | Iterator | Iterator | Loops through Xero transaction records |
| 5 | Google Sheets | Add a Row | Writes each transaction to a temporary CSV sheet |
| 6 | Tools | Sleep | Allows row-writing route to complete before export |
| 7 | Google Sheets | Get Range Values | Retrieves the completed CSV-ready data |
| 8 | Tools | Text Aggregator | Converts rows into CSV text |
| 9 | Asana | Upload an Attachment | Uploads the CSV file to the Asana task |
| 10 | Google Sheets | Clear Values from Range | Clears temporary data after upload |

## Repository Contents

```text
.
├── README.md
├── docs/
│   ├── workflow-overview.md
│   ├── setup-guide.md
│   ├── field-mapping.md
│   ├── test-plan.md
│   └── troubleshooting.md
├── templates/
│   ├── sample-csv-header.csv
│   └── sample-env.example
└── assets/
    └── workflow-screenshot.png
```

## Required Accounts

- Make.com
- Xero account with API access
- Asana workspace/project
- Google Sheets spreadsheet

## Recommended Use Case

This workflow is useful for finance, bookkeeping, operations, and admin teams that need a repeatable way to export transaction data from Xero and attach CSV reports to Asana tasks for review, reconciliation, or client delivery.

## Notes

Do not commit API keys, OAuth tokens, spreadsheet IDs, workspace IDs, or task IDs to GitHub. Store secrets in Make.com connections or environment variables.

## Shared Make.com Workflow

You can view or import the shared Make.com scenario here:

https://us2.make.com/public/shared-scenario/3niw9ogCiHQ/integration-asana-xero
