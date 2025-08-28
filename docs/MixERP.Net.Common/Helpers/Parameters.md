# Parameters.cs Documentation

## Overview

The `Parameters` class in the MixERP.Net.Common.Helpers namespace provides static methods for retrieving application configuration parameters. It serves as a centralized utility for accessing commonly used application settings such as date formats, number formatting preferences, and business identification elements. This class encapsulates the process of reading configuration values from the application's configuration files, specifically from a section named "MixERPParameters".

## Class Documentation

### Parameters

`public static class Parameters`

A static utility class that provides methods to access application configuration parameters. Since this is a static class, it cannot be instantiated, and all its methods are accessed directly through the class name.

#### Dependencies
- Uses [ConfigurationHelper.cs](ConfigurationHelper.md) for retrieving configuration values.

## Method Documentation

### PartyName()

```csharp
public static string PartyName()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured party name value.  
**Description**: Retrieves the configured party name value from the application settings.

**Example Usage**:
```csharp
string partyName = MixERP.Net.Common.Helpers.Parameters.PartyName();
Console.WriteLine($"Party Name: {partyName}");
```

### ShortDateFormat()

```csharp
public static string ShortDateFormat()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured short date format.  
**Description**: Retrieves the configured short date format string from the application settings.

**Example Usage**:
```csharp
string shortDateFormat = MixERP.Net.Common.Helpers.Parameters.ShortDateFormat();
DateTime now = DateTime.Now;
Console.WriteLine($"Current Date (Short Format): {now.ToString(shortDateFormat)}");
```

### LongDateFormat()

```csharp
public static string LongDateFormat()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured long date format.  
**Description**: Retrieves the configured long date format string from the application settings.

**Example Usage**:
```csharp
string longDateFormat = MixERP.Net.Common.Helpers.Parameters.LongDateFormat();
DateTime now = DateTime.Now;
Console.WriteLine($"Current Date (Long Format): {now.ToString(longDateFormat)}");
```

### ShortTimeFormat()

```csharp
public static string ShortTimeFormat()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured short time format.  
**Description**: Retrieves the configured short time format string from the application settings.

**Example Usage**:
```csharp
string shortTimeFormat = MixERP.Net.Common.Helpers.Parameters.ShortTimeFormat();
DateTime now = DateTime.Now;
Console.WriteLine($"Current Time (Short Format): {now.ToString(shortTimeFormat)}");
```

### LongTimeFormat()

```csharp
public static string LongTimeFormat()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured long time format.  
**Description**: Retrieves the configured long time format string from the application settings.

**Example Usage**:
```csharp
string longTimeFormat = MixERP.Net.Common.Helpers.Parameters.LongTimeFormat();
DateTime now = DateTime.Now;
Console.WriteLine($"Current Time (Long Format): {now.ToString(longTimeFormat)}");
```

### ThousandSeparator()

```csharp
public static string ThousandSeparator()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured thousand separator character.  
**Description**: Retrieves the configured thousand separator character from the application settings.

**Example Usage**:
```csharp
string thousandSep = MixERP.Net.Common.Helpers.Parameters.ThousandSeparator();
Console.WriteLine($"Thousand Separator: '{thousandSep}'");
```

### DecimalSeparator()

```csharp
public static string DecimalSeparator()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured decimal separator character.  
**Description**: Retrieves the configured decimal separator character from the application settings.

**Example Usage**:
```csharp
string decimalSep = MixERP.Net.Common.Helpers.Parameters.DecimalSeparator();
Console.WriteLine($"Decimal Separator: '{decimalSep}'");
```

### DecimalPlaces()

```csharp
public static string DecimalPlaces()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured number of decimal places to display.  
**Description**: Retrieves the configured number of decimal places from the application settings.

**Example Usage**:
```csharp
string decimalPlaces = MixERP.Net.Common.Helpers.Parameters.DecimalPlaces();
Console.WriteLine($"Number of Decimal Places: {decimalPlaces}");
```

### CurrencySymbol()

```csharp
public static string CurrencySymbol()
```

**Access Modifier**: `public`  
**Return Type**: `string` - The configured currency symbol.  
**Description**: Retrieves the configured currency symbol from the application settings.

**Example Usage**:
```csharp
string currencySymbol = MixERP.Net.Common.Helpers.Parameters.CurrencySymbol();
decimal amount = 1234.56m;
Console.WriteLine($"Amount: {currencySymbol}{amount}");
```

### GetParameter(string key)

```csharp
private static string GetParameter(string key)
```

**Access Modifier**: `private`  
**Parameters**:
- `key` (string): The configuration key to retrieve from the MixERPParameters section.
**Return Type**: `string` - The value associated with the specified key.  
**Description**: A private helper method that retrieves the value for a specified key from the "MixERPParameters" section of the configuration using the [ConfigurationHelper](ConfigurationHelper.md) class.

This method is internally used by all the public methods to retrieve their respective configuration values.