# VerificationDomain Documentation

## Overview

`VerificationDomain` is a static utility class within MixERP.Net.Common that provides functionality for converting verification type enumerations to their corresponding numeric values. This class serves as a domain translator between the strongly-typed [VerificationType](VerificationType.md) enum and short integer values that represent different verification statuses in the MixERP system. These numeric representations are likely used in database operations and business logic throughout the application.

## Class Documentation

### VerificationDomain

**Namespace**: `MixERP.Net.Common.Models.Transactions`

**Type**: Static class

**Access Modifier**: Public

**Purpose**: Provides utility methods for handling transaction verification statuses by converting between enum values and numeric codes.

## Method Documentation

### GetVerification

**Access Modifier**: Public static

**Purpose**: Converts a [VerificationType](VerificationType.md) enum value to its corresponding numeric short value.

**Parameters**:
- `type` ([VerificationType](VerificationType.md)): The verification type enum value to convert.

**Return Type**: `short`

**Return Value**: A short integer representing the status of verification:
  - `-3`: Rejected verification
  - `-2`: Closed verification
  - `-1`: Withdrawn verification
  - `0`: Unapproved verification (default value)
  - `1`: Approved verification

**Implementation Details**:
1. Uses a switch statement to evaluate the input verification type
2. Returns the corresponding short value based on the verification type
3. Returns `0` (Unapproved) as the default value if the verification type doesn't match any case

**Example Usage**:
```csharp
using MixERP.Net.Common.Models.Transactions;

// Convert approved verification status to its numeric value
short approvedValue = VerificationDomain.GetVerification(VerificationType.Approved);
// approvedValue = 1

// Convert rejected verification status to its numeric value
short rejectedValue = VerificationDomain.GetVerification(VerificationType.Rejected);
// rejectedValue = -3
```

## Related Components

The `VerificationDomain` class works closely with:

- [VerificationType](VerificationType.md) - An enumeration defining the different verification statuses in the system
- [VerificationModel](VerificationModel.md) - Likely uses these numeric values as part of the transaction verification process
- [TranactionMasterModel](TranactionMasterModel.md) - Possibly uses verification statuses to track transaction approvals

## Usage Context

This class plays a critical role in the transaction processing system of MixERP by providing a standardized way to translate between user-friendly verification status enums and their database-friendly numeric representations. These verification statuses are typically used to track approval workflows for financial transactions, determining whether transactions have been approved, rejected, or are still pending review.