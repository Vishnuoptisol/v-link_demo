# ProductModel.cs Documentation

## Overview

`ProductModel.cs` is part of the MixERP.Net Common library, located in the Transactions Models namespace. It defines the `MergeModel` class which serves as a data container for product-related transaction operations, specifically for merging multiple product transactions. This model brings together various aspects needed for a complete transaction, including product details, transaction types, dates, party information, and references.

## Class Documentation

### MergeModel

**Purpose:** Represents a model for merging multiple product transactions in the MixERP system. It contains properties that hold all the necessary information to process a merged transaction.

**Access Modifier:** `public`

**Attributes:**

| Name | Type | Description |
|------|------|-------------|
| `ValueDate` | `DateTime` | The date when the transaction takes effect in the accounting system |
| `PartyCode` | `string` | Identifier code for the party (customer or vendor) involved in the transaction |
| `PriceTypeId` | `int` | Identifier for the pricing scheme applied to the transaction |
| `ReferenceNumber` | `string` | External reference number for the transaction |
| `AgentId` | `int` | Identifier for the sales agent associated with the transaction |
| `View` | `Collection<ProductDetailsModel>` | Collection of product details included in the transaction |
| `StatementReference` | `string` | Additional reference information or notes for the transaction |
| `Book` | `TranBook` | Specifies the transaction book type for the operation |
| `SubBook` | `SubTranBook` | Specifies the sub-transaction book type for the operation |
| `transactionIdCollection` | `Collection<int>` | Collection of transaction IDs to be merged |

**Constructors:** Default constructor (implicitly defined)

## Dependencies

- [ProductDetailsModel.cs](ProductDetailsModel.md): Contains the details for each product line item in the transaction
- [TranBook.cs](TranBook.md): Enum that specifies the type of transaction book (Sales, Purchase, etc.)
- [SubTranBook.cs](SubTranBook.md): Enum that specifies the sub-type of transaction book

## Usage Context

The `MergeModel` class is typically used in transaction processing workflows where multiple related transactions need to be combined into a single transaction. This can happen in various scenarios:

1. Merging multiple sales orders into a single invoice
2. Combining multiple purchase orders for the same vendor
3. Consolidating related inventory movements

When transactions are merged, the system preserves all the necessary information while creating a single transaction record in the database, which is more efficient for processing and reporting.

## Example Usage

```csharp
// Creating a new merge model for combining multiple sales transactions
var mergeModel = new MergeModel
{
    ValueDate = DateTime.Now,
    PartyCode = "CUST-001",
    PriceTypeId = 1, // Regular pricing
    ReferenceNumber = "INV-MERGED-001",
    AgentId = 5, // Sales agent ID
    View = new Collection<ProductDetailsModel>
    {
        new ProductDetailsModel 
        { 
            ItemCode = "ITEM-001",
            Quantity = 10,
            Price = 25.50M
        },
        new ProductDetailsModel 
        { 
            ItemCode = "ITEM-002",
            Quantity = 5,
            Price = 15.75M
        }
    },
    StatementReference = "Merged transaction from multiple orders",
    Book = TranBook.Sales,
    SubBook = SubTranBook.Direct,
    transactionIdCollection = new Collection<int> { 1001, 1002, 1003 }
};

// The mergeModel would then be passed to a business layer method for processing
```

Note: The actual file being documented is `ProductModel.cs` but it contains a class named `MergeModel`. This suggests a possible discrepancy between file naming and class naming, or the file might be incorrectly named in the project structure.