# Troubleshooting

## Xero API Authentication Fails

Possible causes:

- Xero OAuth connection expired.
- User does not have permission for the selected organization.
- Incorrect tenant or organization selected.

Recommended fix:

Reconnect the Xero connection in Make.com and retest the API call.

## No Transactions Returned

Possible causes:

- Date filter is too narrow.
- Account ID is incorrect.
- Endpoint is not the correct Xero object.
- Transactions do not match the selected status.

Recommended fix:

Run the API call with fewer filters first, then add filters back one at a time.

## Google Sheets Rows Are Misaligned

Possible causes:

- Header row does not match Make field mapping.
- Transaction line items contain commas, line breaks, or special characters.
- Text aggregator is not escaping CSV fields properly.

Recommended fix:

Wrap CSV values in quotes and escape internal quotes.

Example:

```text
"{{replace(value; """"; """""")}}"
```

## CSV Uploads Before Rows Are Finished

Possible causes:

- Route 2 runs before Route 1 completes writing rows.
- Sleep duration is too short.

Recommended fix:

Increase the sleep duration or redesign the scenario so CSV generation happens only after row-writing completes.

## Duplicate Attachments in Asana

Possible causes:

- Same task was processed more than once.
- Scenario was manually rerun.

Recommended fix:

Add a custom field or comment to the Asana task after successful export, then filter out already-processed tasks.

## Staging Sheet Does Not Clear

Possible causes:

- Incorrect range selected.
- Google Sheets permission issue.
- Final cleanup module did not execute because of an earlier error.

Recommended fix:

Add error handling and verify the clear range matches the staging rows.
