# Documentation for party-sample.sql

## Overview

The `party-sample.sql` file is a SQL script that provides sample party data for the MixERP application. This script is responsible for populating the `core.parties` table with test data, creating approximately 500 party records with detailed personal information. The script first alters the table structure, adds sample data, and then performs cleanup operations. This file is located in the `MixERP.Net.FrontEnd\db\en-US\` directory and is likely used for development, testing, or demonstration purposes.

## SQL Script Documentation

### Table Alterations

The script begins by adding a new column to the `core.parties` table:

```sql
ALTER TABLE core.parties
ADD shipping_address national character varying(250) NULL;
```

This adds a nullable `shipping_address` column to store the shipping address information for each party.

### Data Insertion

The bulk of the script consists of multiple `INSERT INTO` statements that add sample party records to the `core.parties` table. Each record contains the following fields:

- `party_type_id`: Primarily values 1 or 4, indicating different types of parties
- `first_name`: Person's first name
- `last_name`: Person's last name
- `date_of_birth`: Birthdate (ranging from 1970-01-01 to 1972-12-12)
- `city`: Set to "Yuma" for all records
- `state`: Set to "Colorado" for all records
- `country`: Set to "USA" for all records
- `shipping_address`: Set to "Yuma Colorado USA" for all records
- `phone`: Phone number in format "1-57xxxxx"
- `fax`: Fax number
- `cell`: Cell phone number
- `email`: Email address (format: firstname_lastname@gmail.com)
- `url`: Website URL (format: www.firstname.com)
- `pan_number`: Identification number
- `sst_number`: Sales and Service Tax number
- `cst_number`: Central Sales Tax number
- `allow_credit`: Boolean (true/false) indicating if credit is allowed
- `maximum_credit_period`: Credit period (1 or 0)
- `maximum_credit_amount`: Credit amount (500000 or 0)
- `charge_interest`: Boolean indicating if interest is charged (true for all records)
- `interest_rate`: Set to 5 for all records
- `interest_compounding_frequency_id`: Set to 3 for all records
- `account_id`: Account identifier (varies between records)

### Data Updates

After inserting all the sample records, the script updates the `party_name` field by concatenating last name, first name, and middle name:

```sql
UPDATE core.parties
SET party_name = REPLACE(TRIM(COALESCE(last_name, '') || ', ' || first_name || ' ' || COALESCE(middle_name, '')), ' ', '');
```

This creates a standardized party name format of "LastName, FirstName MiddleName".

### Table Cleanup

Finally, the script removes the previously added `shipping_address` column:

```sql
ALTER TABLE core.parties
DROP column shipping_address;
```

This indicates that the `shipping_address` column was only temporarily needed for data insertion purposes.

## Related Files

The `party-sample.sql` script is part of a larger database setup for the MixERP application. It is related to:

- [mixerp.sql](mixerp.sql): The main database schema file
- [mixerp-db-logic.sql](mixerp-db-logic.sql): Contains database logic implementations
- [sample-data.sql](sample-data.sql): Contains other sample data for the application

## Usage

This script is intended to be executed against a MixERP database to populate the `core.parties` table with sample data. It would typically be used in the following scenarios:

1. Setting up a development environment with test data
2. Creating a demo installation of the MixERP system
3. Testing functionality related to parties (individuals or organizations)

The script appears to be licensed under the Mozilla Public License v. 2.0, as indicated in the header comments.