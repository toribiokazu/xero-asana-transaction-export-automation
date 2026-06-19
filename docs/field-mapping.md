# Field Mapping

Use this file to document the exact Xero-to-CSV field mapping.

## Recommended CSV Columns

```csv
Transaction ID,Date,Contact,Reference,Description,Account Code,Account Name,Type,Status,Currency,Amount,Tax Amount,Total,Tracking Category,Source Task ID
```

## Xero to CSV Mapping

| CSV Column | Xero Field | Notes |
|---|---|---|
| Transaction ID | `BankTransactionID` or transaction ID field | Unique Xero transaction identifier |
| Date | `Date` | Format as YYYY-MM-DD |
| Contact | `Contact.Name` | Customer, vendor, or payee |
| Reference | `Reference` | May be blank |
| Description | `LineItems[].Description` | May require line-item iteration |
| Account Code | `LineItems[].AccountCode` | Used for accounting categorization |
| Account Name | Account lookup or mapped label | Optional if available |
| Type | `Type` | Spend, receive, payment, etc. |
| Status | `Status` | Authorized, draft, voided, etc. |
| Currency | `CurrencyCode` | Example: USD |
| Amount | `LineAmount` or subtotal field | Confirm whether tax-inclusive or tax-exclusive |
| Tax Amount | `TaxAmount` | Optional |
| Total | `Total` | Full transaction total |
| Tracking Category | `Tracking[].Name` | Optional |
| Source Task ID | Asana task ID | Used for audit trail |

## Staging Sheet Notes

The Google Sheet should have headers in row 1. New transaction rows should begin on row 2.

Recommended staging range:

```text
A2:O
```

Recommended export range:

```text
A1:O
```
