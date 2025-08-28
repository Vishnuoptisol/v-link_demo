# StockMasterModel Documentation

## Overview

`StockMasterModel` is a class defined in MixERP.Net.Common that represents stock master transaction data in the MixERP financial system. It serves as a data structure to encapsulate stock-related transaction information, including details about parties, agents, pricing, shipping, and store information. This model is primarily used to handle stock transactions within the MixERP application's transaction processing workflows.

## Class Documentation

### StockMasterModel

**Namespace**: `MixERP.Net.Common.Models.Transactions`

**Access Modifier**: `public`

**Description**: Represents a stock master record in the system, containing essential information about stock-related transactions.

**Properties**:

| Property | Type | Description |
|----------|------|-------------|
| `StockMasterId` | `long` | Unique identifier for the stock master record |
| `TransactionMasterId` | `long` | Foreign key reference to the related transaction master record |
| `PartyCode` | `string` | Code identifying the party (customer or vendor) involved in the transaction |
| `AgentId` | `int` | Identifier for the agent associated with the transaction |
| `PriceTypeId` | `int` | Identifier for the price type applied to the transaction |
| `IsCredit` | `bool` | Flag indicating whether the transaction is on credit |
| `ShipperId` | `int` | Identifier for the shipper handling the delivery |
| `ShippingAddressCode` | `string` | Code referencing the shipping address |
| `ShippingCharge` | `decimal` | The cost charged for shipping |
| `StoreId` | `int` | Identifier for the store involved in the transaction |
| `CashRepositoryId` | `int` | Identifier for the cash repository associated with the transaction |

## Related Models and Dependencies

The `StockMasterModel` class is related to several other components in the system:

- It is associated with transaction records via `TransactionMasterId`, which likely relates to [TranactionMasterModel.cs](../Transactions/TranactionMasterModel.md)
- The `PartyCode` property links to party information defined in the system
- `StockMasterModel` records typically have associated detail records in [StockMasterDetailModel.cs](../Transactions/StockMasterDetailModel.md)
- The model works in conjunction with [TransactionDetailModel.cs](../Transactions/TransactionDetailModel.md) for complete transaction processing
- The `ShippingAddressCode` references shipping addresses likely defined in a related model

## Usage Example

The `StockMasterModel` is typically used in stock transaction operations such as sales, purchases, transfers, and returns. Here is an example of how it might be instantiated:

```csharp
// Create a new stock master record for a sales transaction
var stockMaster = new StockMasterModel
{
    StockMasterId = 0, // Will be assigned by the database
    TransactionMasterId = transactionMaster.TransactionMasterId,
    PartyCode = "CUST-001",
    AgentId = 5,
    PriceTypeId = 1, // Regular price
    IsCredit = true, // Credit sale
    ShipperId = 3,
    ShippingAddressCode = "SHIP-ADDR-100",
    ShippingCharge = 50.00m,
    StoreId = 1,
    CashRepositoryId = 2
};
```

This model would then typically be passed to a data access layer or service method for persistence in the database and further processing.