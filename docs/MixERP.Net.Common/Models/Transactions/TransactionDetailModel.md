# TransactionDetailModel.cs Documentation

## Overview
`TransactionDetailModel.cs` defines a model class that represents the details of a financial transaction in the MixERP accounting system. This class encapsulates information about individual transaction entries, including account codes, monetary amounts (debit and credit), and references. It serves as a data container for transaction line items that make up a complete financial transaction.

## Class Documentation

### TransactionDetailModel
**Namespace:** `MixERP.Net.Common.Models.Transactions`
**Access Modifier:** `public`

A class representing a single line item or entry in a financial transaction. This model is typically used in conjunction with [TranactionMasterModel](MixERP.Net.Common/Models/Transactions/TranactionMasterModel.md) to represent complete transactions in the accounting system.

#### Properties

| Name | Type | Description |
|------|------|-------------|
| `TransactionDetailId` | `long` | The unique identifier for the transaction detail/line item. |
| `TransactionMasterId` | `long` | The foreign key reference to the parent transaction in [TranactionMasterModel](MixERP.Net.Common/Models/Transactions/TranactionMasterModel.md). |
| `AccountCode` | `string` | The accounting code or identifier for the account affected by this transaction. |
| `CashRepositoryName` | `string` | The name of the cash repository involved in the transaction, if applicable. |
| `StatementReference` | `string` | A reference or description for this transaction line item. |
| `Debit` | `decimal` | The debit amount for this transaction line item. |
| `Credit` | `decimal` | The credit amount for this transaction line item. |

## Usage Examples

### Creating a Transaction Detail Entry

```csharp
// Create a new transaction detail/line item
var transactionDetail = new TransactionDetailModel
{
    TransactionDetailId = 1001,
    TransactionMasterId = 500,
    AccountCode = "10001-CASH",
    CashRepositoryName = "Main Cash Register",
    StatementReference = "Payment for Invoice #12345",
    Debit = 1500.00m,
    Credit = 0.00m
};
```

### Using in a Collection of Transaction Details

This model is typically used in collections to represent all line items in a transaction:

```csharp
// Create a list of transaction details
List<TransactionDetailModel> transactionDetails = new List<TransactionDetailModel>();

// Add a debit entry
transactionDetails.Add(new TransactionDetailModel
{
    TransactionDetailId = 1001,
    TransactionMasterId = 500,
    AccountCode = "10001-CASH",
    CashRepositoryName = "Main Cash Register",
    StatementReference = "Cash Sale",
    Debit = 1000.00m,
    Credit = 0.00m
});

// Add a credit entry
transactionDetails.Add(new TransactionDetailModel
{
    TransactionDetailId = 1002,
    TransactionMasterId = 500,
    AccountCode = "40001-SALES",
    CashRepositoryName = null,
    StatementReference = "Cash Sale",
    Debit = 0.00m,
    Credit = 1000.00m
});
```

## Related Files

- [TranactionMasterModel.cs](MixERP.Net.Common/Models/Transactions/TranactionMasterModel.md): Defines the parent/header model for transactions
- [JournalDetailsModel.cs](MixERP.Net.Common/Models/Transactions/JournalDetailsModel.md): Similar model for journal entries
- [TranBook.cs](MixERP.Net.Common/Models/Transactions/TranBook.md): Defines transaction book types used in the system

## Notes

- The `TransactionDetailModel` always works together with a corresponding transaction master record.
- In double-entry accounting, the sum of debits must equal the sum of credits across all transaction detail records that share the same `TransactionMasterId`.
- The `CashRepositoryName` is only populated for cash transactions and might be null for non-cash entries.