# mixerp.sql Documentation

## Overview

The `mixerp.sql` file is a foundational SQL script for the MixERP application that creates the database schema, tables, functions, views, and other database objects required by the system. It establishes the core data structure for an enterprise resource planning (ERP) system, including modules for accounting, inventory management, sales, purchasing, CRM, manufacturing, and more.

This script begins by dropping any existing schemas and creating new schemas for different modules of the application, then proceeds to define the database structure with tables, constraints, indexes, and functions that implement the business logic.

## Schema Structure

The script creates several schemas to organize functionality:

- `audit`: For tracking changes and user activities
- `core`: Core business entities and functionality
- `office`: Organization structure and user management
- `policy`: Access control and verification rules
- `transactions`: Financial and inventory transactions
- `crm`: Customer relationship management
- `mrp`: Manufacturing resource planning

## Major Components

### Verification Statuses

```sql
CREATE TABLE core.verification_statuses
(
    verification_status_id            smallint NOT NULL PRIMARY KEY,
    verification_status_name        national character varying(128) NOT NULL
);
```

This table defines the possible verification states for transactions (-3 = Rejected, -2 = Closed, -1 = Withdrawn, 0 = Unverified, 1 = Automatically Approved, 2 = Approved).

### Custom Data Types

The script creates multiple custom data types to enforce data integrity:

- `transaction_type`: Allows only "Dr" (Debit) or "Cr" (Credit)
- `money_strict`: Money values that must be greater than zero
- `money_strict2`: Money values that must be greater than or equal to zero
- Various other strict integer and decimal types

### User Management System

The script creates tables for user management:

```sql
CREATE TABLE office.users
(
    user_id                 SERIAL NOT NULL PRIMARY KEY,
    role_id                 smallint NOT NULL,
    office_id               integer NOT NULL,
    user_name               national character varying(50) NOT NULL,
    full_name               national character varying(100) NOT NULL,
    password                text NOT NULL,
    audit_user_id           integer NULL REFERENCES office.users(user_id),
    audit_ts                TIMESTAMP WITH TIME ZONE NULL DEFAULT(NOW())
);
```

### Flagging System

Core flags system allows users to mark resources for various purposes:

```sql
CREATE TABLE core.flag_types
(
    flag_type_id              SERIAL NOT NULL PRIMARY KEY,
    flag_type_name            national character varying(24) NOT NULL,
    flag_color                color NOT NULL,
    audit_user_id             integer NULL REFERENCES office.users(user_id),
    audit_ts                  TIMESTAMP WITH TIME ZONE NULL DEFAULT(NOW())
);

CREATE TABLE core.flags
(
    flag_id                   BIGSERIAL NOT NULL PRIMARY KEY,
    user_id                   integer NOT NULL REFERENCES office.users(user_id),
    flag_type_id              integer NOT NULL REFERENCES core.flag_types(flag_type_id),
    resource                  text,
    resource_id               text
);
```

### Office and Organization Structure

```sql
CREATE TABLE office.offices
(
    office_id               SERIAL NOT NULL PRIMARY KEY,
    office_code             national character varying(12) NOT NULL,
    office_name             national character varying(150) NOT NULL,
    nick_name               national character varying(50) NULL,
    registration_date       date NOT NULL,
    currency_code           national character varying(12) NOT NULL,
    /* Additional fields... */
    parent_office_id        integer NULL REFERENCES office.offices(office_id)
);
```

### Chart of Accounts

Extensive accounting structure with account masters, accounts, and accounting functions:

```sql
CREATE TABLE core.account_masters
(
    account_master_id         SERIAL NOT NULL PRIMARY KEY,
    account_master_code       national character varying(3) NOT NULL,
    account_master_name       national character varying(40) NOT NULL    
);

CREATE TABLE core.accounts
(
    account_id              SERIAL NOT NULL PRIMARY KEY,
    account_master_id       integer NOT NULL REFERENCES core.account_masters(account_master_id),
    account_code            national character varying(12) NOT NULL,
    /* Additional fields... */
    parent_account_id       integer NULL REFERENCES core.accounts(account_id)
);
```

### Inventory Management

```sql
CREATE TABLE core.items
(
    item_id                 SERIAL NOT NULL PRIMARY KEY,
    item_code               national character varying(12) NOT NULL,
    item_name               national character varying(150) NOT NULL,
    /* Additional fields... */
    maintain_stock          boolean NOT NULL DEFAULT(true),
    audit_user_id           integer NULL REFERENCES office.users(user_id),
    audit_ts                TIMESTAMP WITH TIME ZONE NULL DEFAULT(NOW())
);

CREATE TABLE core.item_selling_prices
(    
    item_selling_price_id     BIGSERIAL NOT NULL PRIMARY KEY,
    item_id                   integer NOT NULL REFERENCES core.items(item_id),
    /* Additional fields... */
);
```

### Transaction Processing System

```sql
CREATE TABLE transactions.transaction_master
(
    transaction_master_id     BIGSERIAL NOT NULL PRIMARY KEY,
    transaction_counter       integer NOT NULL,
    transaction_code          national character varying(50) NOT NULL,
    book                      national character varying(50) NOT NULL,
    /* Additional fields... */
    verification_status_id    smallint NOT NULL REFERENCES core.verification_statuses(verification_status_id) DEFAULT(0)
);

CREATE TABLE transactions.transaction_details
(
    transaction_detail_id     BIGSERIAL NOT NULL PRIMARY KEY,
    transaction_master_id     bigint NOT NULL REFERENCES transactions.transaction_master(transaction_master_id),
    tran_type                 transaction_type NOT NULL,
    account_id                integer NOT NULL REFERENCES core.accounts(account_id),
    /* Additional fields... */
);
```

### Stock Management System

```sql
CREATE TABLE transactions.stock_master
(
    stock_master_id           BIGSERIAL NOT NULL PRIMARY KEY,
    transaction_master_id     bigint NOT NULL REFERENCES transactions.transaction_master(transaction_master_id),
    /* Additional fields... */
);

CREATE TABLE transactions.stock_details
(
    stock_master_detail_id    BIGSERIAL NOT NULL PRIMARY KEY,
    stock_master_id           bigint NOT NULL REFERENCES transactions.stock_master(stock_master_id),
    tran_type                 transaction_type NOT NULL,
    /* Additional fields... */
);
```

### CRM Tables

```sql
CREATE TABLE crm.lead_sources
(
    lead_source_id          SERIAL NOT NULL PRIMARY KEY,
    lead_source_code        national character varying(12) NOT NULL,
    lead_source_name        national character varying(128) NOT NULL,
    /* Additional fields... */
);

CREATE TABLE crm.lead_statuses
(
    lead_status_id          SERIAL NOT NULL PRIMARY KEY,
    lead_status_code        national character varying(12) NOT NULL,
    lead_status_name        national character varying(128) NOT NULL,
    /* Additional fields... */
);

CREATE TABLE crm.opportunity_stages
(
    opportunity_stage_id    SERIAL  NOT NULL PRIMARY KEY,
    opportunity_stage_code  national character varying(12) NOT NULL,
    opportunity_stage_name  national character varying(50) NOT NULL,
    /* Additional fields... */
);
```

## Key Functions

### Account Management Functions

- `core.has_child_accounts`: Checks if an account has child accounts
- `core.get_cash_account_id`: Gets the cash account ID
- `core.get_account_id_by_account_code`: Finds an account ID by its code
- `core.get_account_id_by_parameter`: Gets an account ID by a parameter name
- `core.get_account_name`: Gets the account name from an ID

### Office and User Functions

- `office.is_parent_office`: Checks if an office is a parent of another office
- `office.get_offices`: Returns a list of offices
- `office.get_office_name_by_id`: Gets an office name by ID
- `office.get_office_id_by_user_id`: Gets an office ID by user ID
- `office.validate_login`: Validates user login credentials

### Unit Conversion Functions

- `core.convert_unit`: Converts between units
- `core.get_root_unit_id`: Gets the base unit ID
- `core.is_parent_unit`: Checks if a unit is parent of another unit
- `core.get_associated_units`: Gets related units

### Transaction Functions

- `transactions.get_new_transaction_counter`: Generates new transaction counters
- `transactions.get_transaction_code`: Creates unique transaction codes
- `transactions.get_invoice_amount`: Calculates invoice totals
- `core.count_item_in_stock`: Counts item quantity in a store

## Policy Management

```sql
CREATE TABLE policy.voucher_verification_policy
(
    user_id                        integer NOT NULL PRIMARY KEY REFERENCES office.users(user_id),
    can_verify_sales_transactions        boolean NOT NULL,
    sales_verification_limit            money NOT NULL,
    /* Additional fields... */
);

CREATE TABLE policy.auto_verification_policy
(
    user_id                        integer NOT NULL PRIMARY KEY REFERENCES office.users(user_id),
    verify_sales_transactions        boolean NOT NULL,
    sales_verification_limit        money NOT NULL,
    /* Additional fields... */
);
```

## Views

The script creates numerous views to simplify data access, including:

- `core.account_view`: Shows account information with parent account details
- `office.user_view`: Shows user information with roles and offices
- `office.login_view`: Shows user login details
- `office.cash_repository_view`: Shows cash repository information
- `core.party_view`: Shows party information with type
- `core.shipping_address_view`: Shows shipping address information
- `core.tax_view`: Shows tax information with accounts
- `transactions.trial_balance_view`: Shows accounting trial balance

## Audit and Tracking

```sql
CREATE TABLE audit.logins
(
    login_id                 BIGSERIAL NOT NULL PRIMARY KEY,
    user_id                  integer NOT NULL REFERENCES office.users(user_id),
    /* Additional fields... */
);

CREATE TABLE audit.failed_logins
(
    failed_login_id          BIGSERIAL NOT NULL PRIMARY KEY,
    user_id                  integer NULL REFERENCES office.users(user_id),
    /* Additional fields... */
);

CREATE TABLE audit.history
(
    activity_id              BIGSERIAL NOT NULL PRIMARY KEY,
    event_ts                 TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT(NOW()),
    principal_user           national character varying(50) NOT NULL DEFAULT(current_user),
    /* Additional fields... */
);
```

## Integration with Other System Components

This SQL script creates the database foundation that is used by the MixERP web application components. The database objects defined here are used by various pages and controls in the application including:

- Login system ([SignIn.aspx](../SignIn.aspx.md))
- Dashboard ([Dashboard/Index.aspx](../Dashboard/Index.aspx.md))
- Sales module ([Sales/Index.aspx](../Sales/Index.aspx.md))
- Purchase module ([Purchase/Index.aspx](../Purchase/Index.aspx.md))
- Inventory management ([Items/Index.aspx](../Items/Index.aspx.md))
- Financial management ([Finance/Index.aspx](../Finance/Index.aspx.md))
- CRM module ([CRM/Index.aspx](../CRM/Index.aspx.md))
- Setup screens ([Setup/Index.aspx](../Setup/Index.aspx.md))

## Sample Data

The script includes sample data for testing and demonstration purposes, including:
- Office structures
- User roles
- Chart of accounts
- Tax types
- Item groups
- CRM lead sources and statuses

## Security Features

The script implements several security features:
- Password storage (encrypted)
- User lockout policies
- Role-based access control
- Audit trail of changes
- Transaction verification workflow

## Summary

The `mixerp.sql` script is a comprehensive database setup script that establishes the foundation for the MixERP application. It creates a multi-schema database structure with tables for all major ERP modules, functions for business logic, views for simplified data access, and security policies to control system access and operations.

The script is designed to be run once during initial setup to create the database structure that will be used by the MixERP.Net.FrontEnd application components.