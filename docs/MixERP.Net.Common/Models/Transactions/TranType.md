# TranType.cs Documentation

## Overview

`TranType.cs` defines an enumeration for transaction types within the MixERP.Net accounting system. This enumeration serves as a foundational component for the financial transaction system, allowing the application to distinguish between debit and credit transactions.

## Namespace

The code is defined within the `MixERP.Net.Common.Models.Transactions` namespace, which is part of the MixERP.Net common models related to financial transactions.

## Enumeration Documentation

### TransactionType

#### Description

The `TransactionType` enumeration represents the basic types of financial transactions in an accounting system. It defines the direction of money movement: either a debit (money going out) or credit (money coming in).

#### Values

- **Debit**: Represents a debit transaction, typically indicating a decrease in assets or an increase in expenses.
- **Credit**: Represents a credit transaction, typically indicating an increase in assets or a decrease in expenses.

## Usage Context

This enumeration is likely used throughout the MixERP application to:

1. Categorize financial transactions
2. Determine how to process transactions in ledgers
3. Establish the direction of money flow in transaction records

## Related Files

This enumeration is likely used in conjunction with:

- [TransactionDetailModel.cs](TransactionDetailModel.md): Models for transaction details that would include transaction type
- [TransactionTypeDomain.cs](TransactionTypeDomain.md): Domain models related to transaction types
- [TranactionMasterModel.cs](TranactionMasterModel.md): Models for transaction master records
- [TranBook.cs](TranBook.md): Models for transaction books that would use these transaction types
- [JournalDetailsModel.cs](JournalDetailsModel.cs): Models for journal entries that require transaction type categorization

## Example Usage

```csharp
// Example of how the enumeration might be used in a transaction
public class TransactionEntry
{
    public decimal Amount { get; set; }
    public TransactionType Type { get; set; }
    
    public void ProcessTransaction()
    {
        if (Type == TransactionType.Debit)
        {
            // Handle debit transaction logic
        }
        else // TransactionType.Credit
        {
            // Handle credit transaction logic
        }
    }
}
```

## License

The code is licensed under the Mozilla Public License, v. 2.0.