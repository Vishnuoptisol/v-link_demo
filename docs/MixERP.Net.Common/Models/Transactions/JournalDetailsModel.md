# JournalDetailsModel Documentation

## Overview
`JournalDetailsModel.cs` defines a model class used to represent individual journal entry details in the MixERP accounting system. This class contains properties that describe a single line item in a journal transaction, including account information, references, and monetary amounts for both debit and credit entries.

## Class Documentation

### JournalDetailsModel
A class that encapsulates the details of a journal entry within a financial transaction.

#### Access Modifier
`public`

#### Properties

| Property | Type | Description |
|----------|------|-------------|
| `AccountCode` | `string` | The code that uniquely identifies the account in the chart of accounts |
| `Account` | `string` | The descriptive name of the account |
| `CashRepository` | `string` | The cash repository associated with the transaction, if applicable |
| `StatementReference` | `string` | A reference or description for the transaction line |
| `Debit` | `decimal` | The debit amount for this journal entry |
| `Credit` | `decimal` | The credit amount for this journal entry |

## Relationships and Dependencies

This model is part of the transactions module within the MixERP.Net.Common namespace. It is likely used in conjunction with other transaction-related models such as:

- [TransactionDetailModel](TransactionDetailModel.md)
- [TranactionMasterModel](TranactionMasterModel.md) (note the typo in the original filename)
- [VerificationModel](VerificationModel.md)

The model may be used in journal voucher operations, general ledger transactions, and financial reporting systems within the MixERP application.

## Usage Examples

### Creating a new journal detail entry

```csharp
JournalDetailsModel journalDetail = new JournalDetailsModel
{
    AccountCode = "1001",
    Account = "Cash in Hand",
    CashRepository = "Main Safe",
    StatementReference = "Payment for invoice #12345",
    Debit = 500.00m,
    Credit = 0.00m
};
```

### Creating a balanced double-entry

```csharp
// First entry (debit)
JournalDetailsModel debitEntry = new JournalDetailsModel
{
    AccountCode = "1001",
    Account = "Cash in Hand",
    CashRepository = "Main Safe",
    StatementReference = "Sale transaction",
    Debit = 1000.00m,
    Credit = 0.00m
};

// Second entry (credit)
JournalDetailsModel creditEntry = new JournalDetailsModel
{
    AccountCode = "4001",
    Account = "Sales Revenue",
    CashRepository = null,
    StatementReference = "Sale transaction",
    Debit = 0.00m,
    Credit = 1000.00m
};

// Add both entries to a collection for processing
List<JournalDetailsModel> journalEntries = new List<JournalDetailsModel> { debitEntry, creditEntry };
```

## Notes

- This model adheres to double-entry bookkeeping principles where total debits must equal total credits for balanced transactions.
- The `CashRepository` property may be null or empty for non-cash accounts.
- This class serves as a data transfer object (DTO) for journal entry details and doesn't contain business logic itself.