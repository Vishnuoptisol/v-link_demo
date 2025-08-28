# sample-data.sql Documentation

## Overview

`sample-data.sql` is a SQL script file that populates the MixERP database with sample data for initial testing and demonstration purposes. The script inserts sample records into three main tables: 
- `core.items`: Inventory items with their pricing and properties
- `office.stores`: Store locations for inventory management
- `office.cash_repositories`: Cash storage locations
- `core.shippers`: Shipping company information

The file is part of MixERP's initialization process, providing essential test data that allows users to immediately interact with the system after installation. It establishes baseline inventory items, stores, cash repositories, and shipping options that are necessary for demonstrating the system's sales, purchase, and inventory management capabilities.

## SQL Script Documentation

### core.items Table Inserts

This section inserts seven sample inventory items into the `core.items` table.

#### Fields Used
- `item_code`: Unique identifier code for the item
- `item_name`: Descriptive name of the item
- `item_group_id`: Foreign key to the item group
- `brand_id`: Foreign key to the brand
- `preferred_supplier_id`: Foreign key to the preferred supplier
- `unit_id`: Foreign key to the unit of measurement
- `hot_item`: Flag indicating if the item is popular/fast-moving ('Yes'/'No')
- `tax_id`: Foreign key to the applicable tax
- `reorder_level`: Quantity threshold for reordering
- `maintain_stock`: Flag indicating if inventory is tracked ('Yes'/'No')
- `cost_price`: Purchase cost of the item
- `selling_price`: Retail price of the item

#### Sample Items Created
1. IBM Thinkpad II Laptop (ITP)
2. Acer Iconia Tab (AIT)
3. Intex Mouse (IXM)
4. Microsoft Office Premium Edition (MSO)
5. Lotus Banking Solution (LBS)
6. CAS Banking Solution (CAS)
7. Samsung Galaxy Tab 10.1 (SGT)

The items range from hardware products (laptops, tablets, mouse) to software solutions (Microsoft Office, banking solutions), with varying price points and inventory management settings.

### office.stores Table Inserts

This section inserts two sample store records into the `office.stores` table.

#### Fields Used
- `office_id`: Foreign key to the office
- `store_code`: Unique identifier code for the store
- `store_name`: Name of the store
- `address`: Physical location of the store
- `store_type_id`: Foreign key to the store type
- `allow_sales`: Boolean flag indicating if sales are permitted from this location

#### Sample Stores Created
1. Store 1: A regular store that allows sales
2. Godown 1: A storage location that does not allow direct sales

These stores would be used in the [Items/Transfer.aspx](../Items/Transfer.aspx.md) and [Items/Adjustment.aspx](../Items/Adjustment.aspx.md) modules for inventory movement and management.

### office.cash_repositories Table Inserts

This section inserts two sample cash repository records into the `office.cash_repositories` table.

#### Fields Used
- `office_id`: Foreign key to the office
- `cash_repository_code`: Unique identifier code for the cash repository
- `cash_repository_name`: Name of the cash repository
- `description`: Brief description of the cash repository

#### Sample Cash Repositories Created
1. Drawer 1: A cash drawer for day-to-day transactions
2. Vault: A secure storage location for cash

These cash repositories are used in the [Finance/JournalVoucher.aspx](../Finance/JournalVoucher.aspx.md) and other financial transaction modules.

### core.shippers Table Insert

This section inserts one default shipping company into the `core.shippers` table.

#### Fields Used
- `company_name`: Name of the shipping company
- `account_id`: Foreign key to the financial account (obtained dynamically via function call)

#### Sample Shipper Created
1. Default: A default shipping company linked to account code 20110

This shipper would be used in the [Sales/DeliveryWithoutOrder.aspx](../Sales/DeliveryWithoutOrder.aspx.md) and [Sales/DeliveryForOrder.aspx](../Sales/DeliveryForOrder.aspx.md) modules.

## Related Files

- [Items/Setup/Items.aspx](../Items/Setup/Items.aspx.md) - Interface for managing inventory items
- [Items/Setup/ItemGroups.aspx](../Items/Setup/ItemGroups.aspx.md) - Interface for managing item categories
- [Items/Setup/Brands.aspx](../Items/Setup/Brands.aspx.md) - Interface for managing product brands
- [POS/Setup/Stores.aspx](../POS/Setup/Stores.aspx.md) - Interface for managing store locations
- [Setup/CashRepositories.aspx](../Setup/CashRepositories.aspx.md) - Interface for managing cash repositories
- [Items/Setup/Shipper.aspx](../Items/Setup/Shipper.aspx.md) - Interface for managing shipping companies
- [db/en-US/mixerp.sql](../db/en-US/mixerp.sql.md) - Main database schema that defines these tables
- [db/en-US/mixerp-db-logic.sql](../db/en-US/mixerp-db-logic.sql.md) - Database functions like `core.get_account_id_by_account_code`

## Usage

This script is typically executed during the initial setup of MixERP or when resetting the system to a demo state. It can be run through:

1. Database management tools like pgAdmin for PostgreSQL
2. During installation process through [Setup/Admin/NewCompany.aspx](../Setup/Admin/NewCompany.aspx.md)
3. Through database restore functionality in [Setup/Admin/Restore.aspx](../Setup/Admin/Restore.aspx.md)

The sample data provides a starting point for testing various functionalities of the MixERP system, particularly sales, purchases, and inventory management functions.