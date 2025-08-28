# TranBook.cs Documentation

## Overview
`TranBook.cs` defines an enumeration that represents transaction book types in the MixERP financial system. This enumeration is used to categorize transactions into specific accounting ledgers, specifically distinguishing between sales and purchase transactions. This is a fundamental component used throughout the transaction processing system in MixERP.

## Namespace
The enumeration is defined within the `MixERP.Net.Common.Models.Transactions` namespace, which contains various models related to financial transactions in the MixERP application.

## Enumeration Documentation

### TranBook

**Type**: Enum  
**Access Modifier**: Public  
**Purpose**: Categorizes financial transactions by their book type (Sales or Purchase)

#### Enum Values

1. **Sales**
   - Represents transactions recorded in the sales ledger
   - Used for tracking revenue-generating transactions

2. **Purchase**
   - Represents transactions recorded in the purchase ledger
   - Used for tracking expense or inventory acquisition transactions

## Usage in the System

This enumeration is utilized throughout the MixERP system to categorize transactions, particularly in:

- Transaction processing workflows
- Financial report generation
- Data filtering and organization in the user interface
- Integration with other transaction-related components like [SubTranBook.cs](SubTranBook.md)
- Transaction record validation in [TransactionDetailModel.cs](TransactionDetailModel.md) and [TranactionMasterModel.cs](TranactionMasterModel.md)

## Related Components

This enumeration works in conjunction with other transaction-related components such as:

- [TranType.cs](TranType.md) - Defines the types of transactions (e.g., credit, debit)
- [TransactionDetailModel.cs](TransactionDetailModel.md) - Contains detailed transaction information
- [TranactionMasterModel.cs](TranactionMasterModel.md) - Represents master transaction records
- [SubTranBook.cs](SubTranBook.md) - Provides more granular categorization of transactions

## Example Usage

```csharp
// Example of using TranBook in a transaction processing method
public void ProcessTransaction(decimal amount, TranBook bookType)
{
    switch(bookType)
    {
        case TranBook.Sales:
            // Handle sales transaction logic
            RecordSalesTransaction(amount);
            break;
        case TranBook.Purchase:
            // Handle purchase transaction logic
            RecordPurchaseTransaction(amount);
            break;
    }
}
```

This simple but essential enumeration helps maintain consistency in transaction categorization across the MixERP system, ensuring that sales and purchase transactions are properly distinguished and processed according to appropriate accounting rules.