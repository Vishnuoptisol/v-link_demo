# VerificationType Enum Documentation

## Overview

`VerificationType` is an enumeration within the MixERP.Net framework that defines different states of verification for transactions. This enum is part of the transaction model system in MixERP.Net.Common and serves as a standardized way to represent the various states a transaction verification can be in throughout its lifecycle.

## Enum Documentation

### VerificationType

**Namespace**: `MixERP.Net.Common.Models.Transactions`

**Description**: Defines the possible verification states for transactions in the MixERP system.

**Access Modifier**: `public`

**Values**:

| Value | Integer | Description |
|-------|---------|-------------|
| `Rejected` | 0 | Indicates that a transaction has been reviewed and rejected. |
| `Closed` | 1 | Indicates that a transaction has been finalized and closed. |
| `Withdrawn` | 2 | Indicates that a transaction has been withdrawn from consideration. |
| `Unapproved` | 3 | Indicates that a transaction is pending approval. |
| `Approved` | 4 | Indicates that a transaction has been reviewed and approved. |

## Usage in the Project

The `VerificationType` enum is used across the MixERP system to track and manage the verification status of financial transactions. It's primarily utilized in the verification workflow process, where transactions may need to go through various approval stages.

### Related Files

This enumeration is closely related to:

- [VerificationModel.cs](VerificationModel.md) - Likely uses this enum to represent the status of verification
- [VerificationDomain.cs](VerificationDomain.md) - May contain domain logic related to verification processes
- [TranactionMasterModel.cs](TranactionMasterModel.md) - May incorporate verification status for transactions

## Example Usage

```csharp
// Creating a new verification record
var verification = new VerificationModel
{
    Status = VerificationType.Unapproved,
    TransactionId = 123,
    // Other properties...
};

// Checking verification status
if(verification.Status == VerificationType.Approved)
{
    // Proceed with approved transaction logic
}
else if(verification.Status == VerificationType.Rejected)
{
    // Handle rejected transaction
}
```

## License

This code is subject to the terms of the Mozilla Public License, v. 2.0.
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).