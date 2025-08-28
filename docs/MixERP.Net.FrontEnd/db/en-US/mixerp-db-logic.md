# MixERP Database Logic SQL Documentation

## Overview
This file contains core database logic for the MixERP application, implemented as PostgreSQL functions. The file includes key functionality for user authentication, item pricing, transaction verification, and reporting. These SQL functions form the backbone of the business logic for the MixERP ERP system, handling everything from login validation to complex financial transaction processing.

## Function Documentation

### 1. `office.can_login()`

#### Purpose
Determines if a user has permission to log into a specific office.

#### Parameters
- `user_id` (integer_strict): The ID of the user attempting to login.
- `office_id` (integer_strict): The ID of the office the user is trying to access.

#### Returns
- `boolean`: TRUE if the user is allowed to login, FALSE otherwise.

#### Implementation Details
The function checks if:
1. The user is not a system user (which is not allowed to login)
2. The office matches the user's default office
3. The office is a parent of the user's assigned office (which allows login)

#### Example Usage
```sql
SELECT office.can_login(5, 3);
```

### 2. `office.sign_in()`

#### Purpose
Authenticates a user login attempt and logs the attempt (successful or failed) for audit purposes.

#### Parameters
- `office_id` (integer_strict): The office ID where the login is attempted.
- `user_name` (text): The username.
- `password` (text): The user's password.
- `browser` (text): The browser information of the client.
- `ip_address` (text): The IP address of the client.
- `remote_user` (text): Remote user information if applicable.

#### Returns
- `integer`: Login ID if successful, 0 if failed.

#### Implementation Details
1. Validates the username and password
2. Checks if the user can log into the requested office
3. Records successful login or logs failure reasons
4. Checks if user is locked out due to failed attempts

#### Example Usage
```sql
SELECT office.sign_in(1, 'admin', 'password123', 'Chrome', '192.168.1.1', '');
```

### 3. `core.get_item_cost_price()`

#### Purpose
Calculates the cost price of an item, considering various pricing rules and unit conversions.

#### Parameters
- `item_id_` (integer): The ID of the item.
- `party_id_` (integer): The party (supplier) ID.
- `unit_id_` (integer): The unit ID for which price is required.

#### Returns
- `money`: The cost price of the item.

#### Implementation Details
1. Checks for an exact match in the item_cost_prices table
2. If not found, looks for prices for other units of the same item
3. If still not found, uses the default cost price from the items table
4. Handles tax adjustments if the price includes tax
5. Applies unit conversion if necessary

#### Example Usage
```sql
SELECT core.get_item_cost_price(101, 25, 5);
```

### 4. `core.get_item_selling_price()`

#### Purpose
Calculates the selling price of an item, considering customer types, price types, and unit conversions.

#### Parameters
- `item_id_` (integer): The ID of the item.
- `party_type_id_` (integer): The party type (customer type) ID.
- `price_type_id_` (integer): The price type ID (e.g., retail, wholesale).
- `unit_id_` (integer): The unit ID for which price is required.

#### Returns
- `money`: The selling price of the item.

#### Implementation Details
1. Checks for an exact match in the item_selling_prices table
2. If not found, looks for prices for other units of the same item
3. If still not found, uses the default selling price from the items table
4. Handles tax adjustments if the price includes tax
5. Applies unit conversion if necessary

#### Example Usage
```sql
SELECT core.get_item_selling_price(101, 2, 1, 5);
```

### 5. `transactions.verification_trigger()`

#### Purpose
A trigger function that enforces transaction verification policies, ensuring proper authorization for transaction approval.

#### Returns
- `TRIGGER`: Returns the NEW row for the trigger.

#### Implementation Details
1. Prevents deletion of transactions
2. Validates which fields can be updated
3. Enforces verification policies based on:
   - Transaction amount
   - User's verification limits
   - Transaction type (sales, purchase, GL)
   - Self-verification rules
4. Updates verification timestamps

#### Trigger Usage
This function is attached as triggers:
```sql
CREATE TRIGGER verification_update_trigger
AFTER UPDATE ON transactions.transaction_master
FOR EACH ROW EXECUTE PROCEDURE transactions.verification_trigger();

CREATE TRIGGER verification_delete_trigger
BEFORE DELETE ON transactions.transaction_master
FOR EACH ROW EXECUTE PROCEDURE transactions.verification_trigger();
```

### 6. `transactions.auto_verify()`

#### Purpose
Automatically verifies transactions based on defined policies, without requiring manual verification.

#### Parameters
- Transaction master ID (bigint): The ID of the transaction to auto-verify.

#### Returns
- `VOID`

#### Implementation Details
1. Determines if the transaction is eligible for auto-verification
2. Checks auto-verification policies for the user who posted the transaction
3. Validates transaction amounts against verification limits
4. Updates verification status if all checks pass

#### Example Usage
```sql
SELECT transactions.auto_verify(5001);
```

### 7. Database Views

#### `transactions.transaction_view`
A view that joins transaction master and details to provide a complete view of transactions.

#### `transactions.verified_transactions_view`
A filtered view showing only verified transactions (verification_status_id > 0).

### 8. `transactions.get_cash_repository_balance()`

#### Purpose
Calculates the current balance of a cash repository by summing verified debits and credits.

#### Parameters
- Repository ID (integer): The cash repository ID.

#### Returns
- `money`: The current balance of the repository.

#### Implementation Details
1. Sums all debits to the repository from verified transactions
2. Sums all credits from the repository from verified transactions
3. Returns debits minus credits as the balance

#### Example Usage
```sql
SELECT transactions.get_cash_repository_balance(3);
```

### 9. `transactions.get_product_view()`

#### Purpose
Returns a filtered view of product transactions based on multiple search criteria.

#### Parameters
- `user_id_` (integer): Current user ID
- `book_` (text): The transaction book
- `office_id_` (integer): Office ID
- `date_from_` (date): Start date for filtering
- `date_to_` (date): End date for filtering
- `office_` (varchar): Office code filter
- `party_` (text): Party name/code filter
- `price_type_` (text): Price type filter
- `user_` (varchar): Username filter
- `reference_number_` (varchar): Reference number filter
- `statement_reference_` (text): Statement reference filter

#### Returns
A table with columns:
- `id` (bigint)
- `value_date` (date)
- `office` (varchar)
- `party` (text)
- `price_type` (text)
- `transaction_ts` (timestamp)
- `user` (varchar)
- `reference_number` (varchar)
- `statement_reference` (text)
- `flag_color` (text)

#### Implementation Details
1. Uses a recursive CTE to fetch the office hierarchy
2. Joins multiple tables to get transaction details
3. Applies filters based on all parameters
4. Returns up to 100 records matching the criteria

#### Example Usage
```sql
SELECT * FROM transactions.get_product_view(1, 'Sales', 2, '2023-01-01', '2023-12-31', '', '', '', '', '', '');
```

## Related Files

This file is part of the database schema and depends on:
- [mixerp.sql](mixerp.sql.md) - Contains the base database schema
- [sample-data.sql](sample-data.sql.md) - Contains sample data for testing

## Notes

- The database logic is implemented in PostgreSQL's procedural language PL/pgSQL
- Functions use strict typing (integer_strict) to ensure data integrity
- Transaction verification follows a multi-layered approval system with configurable limits
- Pricing functions handle complex pricing scenarios including customer-specific pricing and unit conversions