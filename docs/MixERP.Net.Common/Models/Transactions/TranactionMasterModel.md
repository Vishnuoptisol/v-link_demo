# TransactionMasterModel Documentation

## Overview
This file defines the `TransactionMasterModel` class within the `MixERP.Net.Common.Models.Transactions` namespace. The class serves as a data model for transaction master records in the MixERP financial system. It represents the header or main information of a financial transaction, containing essential metadata such as transaction identifiers, dates, references, and verification status.

## Class Documentation

### TransactionMasterModel

**Purpose:** Represents the master record of a financial transaction in the MixERP system.

**Access Modifier:** `public`

**Attributes:**

| Attribute | Type | Description |
|-----------|------|-------------|
| TransactionMasterId | `long` | Unique identifier for the transaction master record |
| TransactionCounter | `int` | Sequential counter for the transaction |
| TransactionCode | `string` | Unique code identifier for the transaction |
| Book | `string` | The accounting book where the transaction is recorded |
| ValueDate | `DateTime` | The effective date of the transaction for accounting purposes |
| TransactionTimestamp | `DateTime` | The actual timestamp when the transaction was created |
| LogOnId | `long` | The login session identifier associated with this transaction |
| SysUserId | `int` | The system user ID who created or is responsible for the transaction |
| OfficeId | `int` | The office ID where the transaction was created |
| CostCenterId | `int` | The cost center ID associated with this transaction |
| ReferenceNumber | `string` | External reference number for the transaction |
| StatementReference | `string` | Description or statement reference for the transaction |
| Verification | `VerificationType` | The verification status of the transaction, using the [VerificationType](VerificationType.md) enum |

## Related Components

- **Verification Type**: This class utilizes the `VerificationType` enum defined in [VerificationType.cs](VerificationType.md) which defines the possible verification statuses for transactions.

## Usage Example

The `TransactionMasterModel` class is typically used in conjunction with other transaction-related models like [TransactionDetailModel](TransactionDetailModel.md) to form a complete representation of a financial transaction in the system.

```csharp
// Example usage of TransactionMasterModel
var transactionMaster = new TransactionMasterModel
{
    TransactionMasterId = 1001,
    TransactionCounter = 1,
    TransactionCode = "TRX-2023-00001",
    Book = "Sales",
    ValueDate = DateTime.Now.Date,
    TransactionTimestamp = DateTime.Now,
    LogOnId = 123456,
    SysUserId = 45,
    OfficeId = 2,
    CostCenterId = 10,
    ReferenceNumber = "INV-2023-00123",
    StatementReference = "Sales transaction for customer XYZ",
    Verification = VerificationType.Approved
};
```

## Relationships with Other Components

This model is typically the parent entity for transaction detail records, which would be represented by the [TransactionDetailModel](TransactionDetailModel.md). Together, they form a master-detail relationship for storing complete financial transaction data.

The model integrates with the transaction processing system defined by other components such as [TranBook](TranBook.md) and may be used within verification workflows represented by the [VerificationModel](VerificationModel.md).