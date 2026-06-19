# Test Plan

## Test Case 1: Scenario Trigger

**Action:** Complete a test task in Asana.  
**Expected Result:** Make.com scenario starts successfully.

## Test Case 2: Xero API Call

**Action:** Run the Xero module.  
**Expected Result:** Xero returns transaction records without authentication errors.

## Test Case 3: Iterator

**Action:** Pass transaction records into the iterator.  
**Expected Result:** Each transaction is processed as a separate bundle.

## Test Case 4: Google Sheets Add Row

**Action:** Run Route 1.  
**Expected Result:** Each transaction appears as a row in the staging sheet.

## Test Case 5: CSV Aggregation

**Action:** Run Route 2 after rows are written.  
**Expected Result:** Text aggregator creates properly formatted CSV content.

## Test Case 6: Asana Attachment Upload

**Action:** Upload the generated CSV to the Asana task.  
**Expected Result:** CSV file appears as an attachment on the source task.

## Test Case 7: Cleanup

**Action:** Confirm final module clears the Google Sheet range.  
**Expected Result:** Temporary transaction rows are removed after the CSV is uploaded.

## Test Case 8: Empty Result Handling

**Action:** Run with a Xero query that returns no transactions.  
**Expected Result:** Scenario should not upload an empty or broken CSV unless that behavior is intentional.

## Test Case 9: Duplicate Run Prevention

**Action:** Run the same completed task twice.  
**Expected Result:** Scenario should avoid creating duplicate CSV attachments, or duplicates should be clearly timestamped.
