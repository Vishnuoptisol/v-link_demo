# MixERP.Net.FrontEnd/db/en-US/mixerp.bak.sql Documentation

## Overview

`mixerp.bak.sql` is a comprehensive SQL script that defines the database structure for the MixERP application. It contains the schema definitions, tables, views, functions, triggers, and indexes required to support the MixERP ERP (Enterprise Resource Planning) system. The script establishes the foundation for various business modules including accounting, inventory, sales, purchases, CRM, and manufacturing.

The script organizes the database into multiple schemas including:
- `audit` - For tracking system activities and changes
- `core` - For core business entities and functions
- `office` - For organizational structure definitions
- `policy` - For access control and business rules
- `transactions` - For financial and inventory transactions
- `crm` - For customer relationship management
- `mrp` - For manufacturing resource planning

The script also includes initialization of essential system data, such as default accounts, units of measure, currencies, and user roles.

## Schema Structure

### Schemas Defined

The script begins by dropping existing schemas if they exist and then creating fresh ones:

```sql
DROP SCHEMA IF EXISTS audit CASCADE;
DROP SCHEMA IF EXISTS core CASCADE;
DROP SCHEMA IF EXISTS office CASCADE;
DROP SCHEMA IF EXISTS policy CASCADE;
DROP SCHEMA IF EXISTS transactions CASCADE;
DROP SCHEMA IF EXISTS crm CASCADE;
DROP SCHEMA IF EXISTS mrp CASCADE;

CREATE SCHEMA audit;
CREATE SCHEMA core;
CREATE SCHEMA office;
CREATE SCHEMA policy;
CREATE SCHEMA transactions;
CREATE SCHEMA crm;
CREATE SCHEMA mrp;
```

### Core Data Types and Domains

The script defines several custom data types and domains for ensuring data integrity:

1. **transaction_type** - A domain restricting values to 'Dr' (Debit) or 'Cr' (Credit)
2. **money_strict** - A domain ensuring money values are greater than zero
3. **money_strict2** - A domain ensuring money values are greater than or equal to zero
4. **integer_strict** - A domain ensuring integer values are greater than zero
5. **integer_strict2** - A domain ensuring integer values are greater than or equal to zero
6. **decimal_strict** - A domain ensuring decimal values are greater than zero
7. **decimal_strict2** - A domain ensuring decimal values are greater than or equal to zero
8. **image_path** - A domain for storing image file paths

## Key Database Tables

### User Management and Authentication

#### office.users
Defines user accounts within the system:
- Primary identification fields: `user_id`, `user_name`, `full_name`
- Authentication fields: `password`
- Organizational fields: `role_id`, `office_id`
- Auditing fields: `audit_user_id`, `audit_ts`

#### office.roles
Defines user roles for access control:
- Fields include `role_id`, `role_code`, `role_name`
- Special flags include `is_admin` and `is_system`

#### audit.logins
Tracks user login activity:
- Records login time, browser information, and IP address

#### audit.failed_logins
Tracks failed login attempts:
- Records failure details including browser, IP, and timestamps

#### policy.lock_outs
Manages account lockouts after multiple failed login attempts:
- Defines lockout period and timing

### Organizational Structure

#### office.offices
Defines business locations/branches:
- Includes address, contact details, and organizational hierarchy
- References `core.currencies` for default currency

#### office.departments
Defines departments within the organization:
- Basic department identifiers and names

#### office.stores
Defines physical inventory locations:
- Links to offices with fields for `store_code`, `store_name`, `address`
- Includes `store_type_id` reference

#### office.cost_centers
Defines cost centers for accounting:
- Provides structure for expense allocation and tracking

### Finance and Accounting

#### core.account_masters
Defines account master categories:
- Examples include "Balance Sheet A/C" and "Profit and Loss A/C"

#### core.accounts
Defines the chart of accounts:
- Links accounts to `account_masters`
- Provides hierarchical structure with `parent_account_id`
- Includes flags for account types, system accounts, and cash accounts

#### core.currencies
Defines currencies used in the system:
- Includes currency code, name, and symbol

#### core.bank_accounts
Extends account information for bank accounts:
- Links to core.accounts
- Includes bank details, account numbers, and branch information

### Inventory Management

#### core.units
Defines units of measure:
- Basic unit identifiers like piece, kg, etc.

#### core.compound_units
Defines conversion between units:
- Maps relationships between units (e.g., 12 pieces = 1 dozen)

#### core.items
Defines inventory items:
- Item identification, pricing, and categorization
- Links to suppliers, units, taxes, and brands

#### core.item_groups
Organizes items into groups:
- Provides categorization with flags for sales/purchase exclusions

#### core.item_selling_prices
Defines selling prices for items:
- Price variations based on units, customer types, etc.

#### core.item_cost_prices
Defines cost prices for items:
- Cost variations based on suppliers, etc.

### Parties (Customers, Suppliers)

#### core.party_types
Defines types of business relationships:
- Examples include suppliers, customers, agents

#### core.parties
Defines entities with whom business is conducted:
- Includes individuals or organizations who are customers, suppliers, etc.
- Stores contact details, credit limits, etc.

#### core.shipping_addresses
Defines shipping locations for parties:
- Multiple addresses can be linked to a single party

### Transactions

#### transactions.transaction_master
Records the header information for all financial transactions:
- Links transactions to users, offices, and books
- Tracks verification status

#### transactions.transaction_details
Records the detailed entries for financial transactions:
- Debit/credit entries with account references
- Amount and reference information

#### transactions.stock_master
Records the header information for inventory transactions:
- Links to transaction_master
- Includes party, agent, and shipping details

#### transactions.stock_details
Records the detailed entries for inventory transactions:
- Item quantities, prices, discounts, and taxes

### CRM (Customer Relationship Management)

#### crm.lead_sources
Defines sources of sales leads:
- Examples include agents, cold calls, events

#### crm.lead_statuses
Defines statuses for tracking leads:
- Examples include cool, in progress, qualified

#### crm.opportunity_stages
Defines stages in the sales opportunity cycle:
- Examples include prospecting, negotiation, closed won/lost

## Key Database Functions

### User and Authentication Functions

1. **office.validate_login** - Authenticates user credentials
2. **policy.is_locked_out_till** - Checks if a user account is locked
3. **policy.perform_lock_out** - Triggers account lockout after failed attempts

### Transaction Management Functions

1. **transactions.get_new_transaction_counter** - Generates transaction counter for a date
2. **transactions.get_transaction_code** - Generates unique transaction codes
3. **transactions.get_invoice_amount** - Calculates total invoice amount

### Inventory Functions

1. **core.convert_unit** - Converts between different units of measure
2. **core.get_associated_units** - Returns compatible units for an item
3. **core.count_item_in_stock** - Counts available inventory for an item

### Account Functions

1. **core.has_child_accounts** - Checks if an account has child accounts
2. **core.get_cash_account_id** - Returns the default cash account
3. **core.disable_editing_sys_type** - Prevents modification of system accounts

## Database Views

The script creates numerous views for simplified data access, including:

1. **core.account_view** - Provides a simplified view of the account structure
2. **core.party_view** - Combines party details with their types
3. **office.login_view** - Provides user login information with related office details
4. **office.user_view** - User information with role and office details
5. **transactions.trial_balance_view** - Summarizes debit and credit balances

## Data Initialization

The script initializes essential reference data, including:

1. **Verification Statuses** - Statuses like Unverified, Rejected, Approved
2. **Default Currencies** - NPR (Nepali Rupees) and USD (US Dollar)
3. **Default Office** - "Planet Earth Solutions" with branches
4. **User Roles** - System, Administrator, and various business roles
5. **Chart of Accounts** - Complete accounting structure
6. **Default Items and Units** - Basic inventory structure
7. **Default Tax Types** - VAT and sales tax configurations
8. **CRM Reference Data** - Lead sources, statuses, and opportunity stages

## Conclusion

The `mixerp.bak.sql` script establishes a comprehensive database foundation for the MixERP application. It defines the data structures needed to support multi-office operations, financial accounting, inventory management, sales, purchasing, and customer relationship management. The script includes numerous integrity constraints, triggers, and functions to ensure data consistency and business rule enforcement within the application.

This database structure supports the web-based interface defined in the other files of the MixERP.Net.FrontEnd project, providing the data persistence layer for the entire ERP system.