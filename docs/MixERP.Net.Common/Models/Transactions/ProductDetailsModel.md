# ProductDetailsModel.cs Documentation

## Overview
The `ProductDetailsModel` class is defined in the MixERP.Net.Common library, specifically in the Models.Transactions namespace. This model represents details of a product in a transaction, containing properties for product identification, quantity, pricing information, and calculations like discount, tax, and total amounts. It serves as a data structure for handling product line items in sales, purchase, or other transaction-related operations throughout the MixERP application.

## Class Documentation

### ProductDetailsModel
**Namespace**: `MixERP.Net.Common.Models.Transactions`  
**Access Modifier**: `public`  
**Description**: Represents a detailed view of a product item within a transaction, including pricing and quantity information.

#### Properties

| Property | Type | Description |
|----------|------|-------------|
| ItemCode | string | The unique code that identifies the product |
| ItemName | string | The name or description of the product |
| Quantity | int | The quantity of the product in the transaction |
| Unit | string | The unit of measurement for the product (e.g., each, kg, liter) |
| Price | decimal | The unit price of the product |
| Amount | decimal | The raw amount (typically Price × Quantity) |
| Discount | decimal | The discount amount applied to the product |
| Subtotal | decimal | The amount after discount (typically Amount - Discount) |
| Rate | decimal | Likely a tax rate or conversion rate applied to the product |
| Tax | decimal | The tax amount calculated for this product |
| Total | decimal | The final total amount after all calculations (Subtotal + Tax) |

## Related Components

The `ProductDetailsModel` is often used in transaction processing throughout the MixERP system. It may be used with:

- [ProductModel.cs](ProductModel.md) - A model that might use `ProductDetailsModel` as part of its collection
- [StockMasterDetailModel.cs](StockMasterDetailModel.md) - For stock transaction details
- [TransactionDetailModel.cs](TransactionDetailModel.md) - For general transaction details

## Usage Examples

### Creating a new product line item

```csharp
var productDetail = new ProductDetailsModel
{
    ItemCode = "ITEM-001",
    ItemName = "Laptop Computer",
    Quantity = 2,
    Unit = "Each",
    Price = 1200.00m,
    Amount = 2400.00m,
    Discount = 200.00m,
    Subtotal = 2200.00m,
    Rate = 0.10m,  // 10% tax rate
    Tax = 220.00m,
    Total = 2420.00m
};
```

### Using in a collection of transaction items

```csharp
List<ProductDetailsModel> orderItems = new List<ProductDetailsModel>();
// Add multiple products to the order
orderItems.Add(productDetail);
```

## Notes

- The `ProductDetailsModel` is designed to contain all necessary information about a product line item in a transaction.
- Calculations between properties (e.g., Price × Quantity = Amount) are not automatically performed within this model; they must be set explicitly.
- This model appears to be primarily used for data transfer and representation rather than business logic.