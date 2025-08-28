# Switches.cs Documentation

## Overview

The `Switches` class is a utility static class that provides access to configuration switches used throughout the MixERP application. It abstracts the process of reading boolean configuration values from the application's configuration file, providing simple methods that return boolean values indicating whether specific features are enabled or disabled.

## Class Documentation

### Switches

- **Namespace**: `MixERP.Net.Common.Helpers`
- **Type**: `static class`
- **Access Modifier**: `public`
- **Purpose**: To provide centralized access to application-level configuration switches

## Method Documentation

### AllowNonSupplierInPurchase

```csharp
public static bool AllowNonSupplierInPurchase()
```

- **Access Modifier**: `public`
- **Return Type**: `bool`
- **Purpose**: Determines if non-suppliers are allowed in purchase transactions.
- **Description**: Retrieves the "AllowNonSupplierInPurchase" switch value from the application configuration.
- **Example Usage**:
  ```csharp
  if (Switches.AllowNonSupplierInPurchase())
  {
      // Allow purchase transactions with entities not marked as suppliers
  }
  ```

### AllowSupplierInSales

```csharp
public static bool AllowSupplierInSales()
```

- **Access Modifier**: `public`
- **Return Type**: `bool`
- **Purpose**: Determines if suppliers are allowed in sales transactions.
- **Description**: Retrieves the "AllowSupplierInSales" switch value from the application configuration.
- **Example Usage**:
  ```csharp
  if (Switches.AllowSupplierInSales())
  {
      // Allow sales transactions with supplier entities
  }
  ```

### AllowParentAccountInGLTransaction

```csharp
public static bool AllowParentAccountInGLTransaction()
```

- **Access Modifier**: `public`
- **Return Type**: `bool`
- **Purpose**: Determines if parent accounts can be used directly in General Ledger transactions.
- **Description**: Retrieves the "AllowParentAccountInGLTransaction" switch value from the application configuration.
- **Example Usage**:
  ```csharp
  if (Switches.AllowParentAccountInGLTransaction())
  {
      // Allow parent accounts to be used in GL transactions
  }
  ```

### EnableAutoVerification

```csharp
public static bool EnableAutoVerification()
```

- **Access Modifier**: `public`
- **Return Type**: `bool`
- **Purpose**: Determines if automatic verification of transactions is enabled.
- **Description**: Retrieves the "EnableAutoVerification" switch value from the application configuration.
- **Example Usage**:
  ```csharp
  if (Switches.EnableAutoVerification())
  {
      // Automatically verify transactions without manual intervention
  }
  ```

### TaxAfterDiscount

```csharp
public static bool TaxAfterDiscount()
```

- **Access Modifier**: `public`
- **Return Type**: `bool`
- **Purpose**: Determines if tax should be calculated after applying discounts.
- **Description**: Retrieves the "TaxAfterDiscount" switch value from the application configuration.
- **Example Usage**:
  ```csharp
  if (Switches.TaxAfterDiscount())
  {
      // Calculate tax based on the discounted amount
  }
  else
  {
      // Calculate tax based on the original amount before discount
  }
  ```

### GetSwitch

```csharp
private static bool GetSwitch(string key)
```

- **Access Modifier**: `private`
- **Return Type**: `bool`
- **Parameters**:
  - `key` (string): The name of the configuration switch to retrieve.
- **Purpose**: Internal method to retrieve the boolean value of a specified switch from the application configuration.
- **Description**: 
  1. Gets the configuration value using the [ConfigurationHelper](ConfigurationHelper.md) class.
  2. Checks if the value is null or whitespace, returning false in that case.
  3. Returns true if the value is the string "true", otherwise returns false.
- **Example Usage**:
  ```csharp
  // Internal method used by public switch methods
  bool isFeatureEnabled = GetSwitch("FeatureName");
  ```

## Dependencies

- [ConfigurationHelper.cs](ConfigurationHelper.md): Used to retrieve configuration values from the application's configuration file.

## Configuration

These switches must be configured in the application's configuration file under the "MixERPSwitches" section. Each switch should have a key matching the method name (without the "get" prefix) and a value of either "true" or "false".

Example configuration:
```xml
<MixERPSwitches>
  <add key="AllowNonSupplierInPurchase" value="true" />
  <add key="AllowSupplierInSales" value="false" />
  <add key="AllowParentAccountInGLTransaction" value="false" />
  <add key="EnableAutoVerification" value="true" />
  <add key="TaxAfterDiscount" value="true" />
</MixERPSwitches>
```