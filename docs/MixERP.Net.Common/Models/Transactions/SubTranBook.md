# SubTranBook.cs Documentation

## Overview

`SubTranBook.cs` defines an enumeration for different types of subsidiary transaction books in the MixERP accounting system. These transaction book types represent various stages in a business transaction flow, from initial quotation to final invoice. The enumeration is part of the `MixERP.Net.Common.Models.Transactions` namespace and serves as a foundation for classifying transaction types throughout the system.

## Enum Documentation

### SubTranBook

**Namespace**: `MixERP.Net.Common.Models.Transactions`
**Access Modifier**: `public`
**Type**: `enum`

This enumeration categorizes different types of subsidiary transaction books that track specific stages or types of business transactions.

#### Values

| Value | Description |
|-------|-------------|
| Direct | Represents direct transactions that may not follow the complete order-to-invoice workflow |
| Quotation | Represents price quotations given to customers before formal orders |
| Order | Represents customer orders *(Readonly)* |
| Delivery | Represents product deliveries to customers *(Readonly)* |
| Receipt | Represents receipts issued for payments *(Readonly)* |
| Invoice | Represents final billing documents sent to customers |

## Related Files

This enumeration is used across the MixERP transaction processing system and relates to:

- [TranBook.cs](TranBook.md) - The parent transaction book enumeration
- [TransactionDetailModel.cs](TransactionDetailModel.md) - Model that likely uses this enum for transaction categorization
- [TranactionMasterModel.cs](TranactionMasterModel.md) - Master transaction records that would be categorized using this enum
- [StockMasterModel.cs](StockMasterModel.md) - Inventory transactions that would reference these transaction types
- [ProductModel.cs](ProductModel.md) - Products involved in these various transaction types

## Usage Examples

### Example: Categorizing a Transaction

```csharp
// Example of how this enum might be used in the system
public class TransactionExample
{
    public void ProcessTransaction(SubTranBook bookType)
    {
        switch(bookType)
        {
            case SubTranBook.Direct:
                // Process a direct transaction
                break;
            case SubTranBook.Quotation:
                // Process a quotation
                break;
            case SubTranBook.Order:
                // Handle an order transaction
                break;
            case SubTranBook.Delivery:
                // Process a delivery transaction
                break;
            case SubTranBook.Receipt:
                // Handle a receipt transaction
                break;
            case SubTranBook.Invoice:
                // Process an invoice transaction
                break;
        }
    }
}
```

### Notes

- Values marked as *(Readonly)* in comments suggest these transaction types may be for reference or reporting purposes only and may not be directly modifiable through the standard interface.
- The `SubTranBook` enum is likely used in transaction filtering, reporting, and processing workflows throughout the MixERP system.