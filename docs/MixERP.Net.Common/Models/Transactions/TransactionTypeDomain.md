# TransactionTypeDomain.cs Documentation

## Overview
`TransactionTypeDomain.cs` defines a static utility class `TransactionTypeDomain` in the MixERP.Net system that provides functionality to convert a transaction type enumeration to its domain representation. Specifically, it maps debit and credit transaction types to their common accounting abbreviations ("Dr" for debit and "Cr" for credit).

## Class Documentation

### TransactionTypeDomain
```csharp
public static class TransactionTypeDomain
```

**Purpose:** Converts transaction type enumerations to their domain-specific string representations.

**Access Modifier:** `public static`

**Attributes:** None

**Constructors:** None (static class)

## Method Documentation

### GetDomain
```csharp
public static string GetDomain(TransactionType type)
```

**Purpose:** Converts a transaction type enumeration value to its corresponding accounting abbreviation.

**Access Modifier:** `public static`

**Parameters:**
- `type` (TransactionType): The transaction type to convert, either debit or credit.

**Return Type:** `string`
- Returns "Dr" for `TransactionType.Debit`
- Returns "Cr" for `TransactionType.Credit`

**Exceptions:**
- `InvalidOperationException`: Thrown when an unsupported transaction type is provided, with a localized error message retrieved from the resources.

**Example Usage:**
```csharp
string domain = TransactionTypeDomain.GetDomain(TransactionType.Debit);
// Result: "Dr"
```

## Dependencies

- Utilizes the `TransactionType` enumeration, defined in [`TranType.cs`](TranType.cs)
- Uses the `LocalizationHelper` for retrieving localized error messages from [`LocalizationHelper.cs`](../../Helpers/LocalizationHelper.cs)

## Notes
- This class follows the common accounting convention of representing debits as "Dr" and credits as "Cr"
- The implementation handles only the specifically defined transaction types and throws an exception for any other values
- The error message for unknown transaction types is retrieved from a localization resource file using the `LocalizationHelper`