# StockMasterDetailModel Documentation

## Overview

The `StockMasterDetailModel` class is part of the MixERP.Net.Common library, specifically residing in the Models.Transactions namespace. This model represents the details of stock transactions in the MixERP system. It captures information about individual line items in a stock transaction, including product information, pricing, quantity, and tax details. This model is essential for stock management operations such as purchases, sales, transfers, and adjustments.

## Class Documentation

### StockMasterDetailModel

A class that models the detailed information about an item in a stock transaction.

#### Access Modifier
`public`

#### Properties

| Property | Type | Description |
|----------|------|-------------|
| `StockMasterDetailId` | `long` | The unique identifier for this stock transaction detail record |
| `StockMasterId` | `long` | The identifier for the parent stock transaction master record that this detail belongs to |
| `TransactionType` | [`TransactionType`](TransactionTypeDomain.md) | The type of transaction being performed (e.g., purchase, sale, transfer) |
| `StoreId` | `int` | The identifier of the store where the transaction is taking place |
| `ItemCode` | `string` | The code that identifies the inventory item |
| `Quantity` | `int` | The number of items involved in the transaction |
| `UnitName` | `string` | The unit of measurement for the item (e.g., piece, box, kg) |
| `Price` | `decimal` | The unit price of the item |
| `Discount` | `decimal` | The discount amount applied to this item |
| `TaxRate` | `decimal` | The tax rate percentage applicable to this item |
| `Tax` | `decimal` | The calculated tax amount for this item |

## Relationships

The `StockMasterDetailModel` class is related to the following classes:

- [`StockMasterModel`](StockMasterModel.md): The `StockMasterId` property links a detail record to its master record.
- [`TransactionType`](TransactionTypeDomain.md): The `TransactionType` property indicates what type of stock transaction is being performed.

## Usage Examples

### Creating a New Stock Transaction Detail

```csharp
// Example: Creating a new item detail for a purchase transaction
var detailItem = new StockMasterDetailModel
{
    StockMasterDetailId = 0, // Will be assigned by database
    StockMasterId = masterTransactionId,
    TransactionType = TransactionType.Purchase,
    StoreId = 1,
    ItemCode = "ITEM-001",
    Quantity = 10,
    UnitName = "Piece",
    Price = 19.99m,
    Discount = 2.00m,
    TaxRate = 7.5m,
    Tax = 13.49m // (19.99 * 10 - 2.00) * 0.075
};
```

### Calculating Line Total

While not included in the model itself, the line total for a stock detail record can be calculated as:

```csharp
decimal lineTotal = (detail.Quantity * detail.Price) - detail.Discount + detail.Tax;
```

## Notes

- The `StockMasterDetailModel` typically works in conjunction with the [`StockMasterModel`](StockMasterModel.md) which contains header information for the transaction.
- The `TransactionType` property is an enum from the [`TransactionTypeDomain`](TransactionTypeDomain.md) that defines various types of stock transactions supported by the system.
- This model is designed to work within MixERP's inventory management subsystem and is likely used in purchase, sales, and inventory adjustment operations.