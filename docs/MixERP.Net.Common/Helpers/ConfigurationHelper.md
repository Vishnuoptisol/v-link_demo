# ConfigurationHelper.cs Documentation

## Overview

The `ConfigurationHelper` class provides utility methods to access configuration data from application configuration sections. It simplifies the process of retrieving configuration values by section and key names, encapsulating the standard .NET Configuration API calls.

Located in the MixERP.Net.Common library, this helper is a foundational component that can be used across the application to access configuration settings in a standardized way.

## Class Documentation

### ConfigurationHelper

```csharp
public static class ConfigurationHelper
```

**Purpose**: A static utility class that provides methods to access configuration values from specified sections of the application configuration.

**Access Modifier**: `public`

**Attributes**:
- `static`: This class cannot be instantiated and all methods are accessed directly through the class name.

## Method Documentation

### GetSectionKey

```csharp
public static string GetSectionKey(string sectionName, string keyName)
```

**Purpose**: Retrieves a specific configuration value from a named section in the application configuration.

**Access Modifier**: `public static`

**Parameters**:
- `sectionName` (string): The name of the configuration section to retrieve.
- `keyName` (string): The key name within the section whose value is to be retrieved.

**Return Type**: `string` - The value of the specified key in the specified section, or an empty string if the section or key doesn't exist.

**Process**:
1. Retrieves the named configuration section using `ConfigurationManager.GetSection`
2. Casts the returned object to a `NameValueCollection`
3. If the section exists (not null), returns the value for the specified key
4. If the section doesn't exist or the key is not found, returns an empty string

**Example Usage**:
```csharp
// Assuming a configuration section named "DbParameters" with a key named "Server"
string serverName = ConfigurationHelper.GetSectionKey("DbParameters", "Server");

// If the section or key doesn't exist, an empty string is returned
string nonExistentValue = ConfigurationHelper.GetSectionKey("NonExistentSection", "NonExistentKey"); // Returns ""
```

## Dependencies

This class depends on:
- `System.Collections.Specialized` - For the `NameValueCollection` type
- `System.Configuration` - For accessing the application configuration

The class is used in conjunction with XML configuration files like those found in the MixERP.Net.FrontEnd project's [Resource/Configuration](../Resource/Configuration) directory, particularly files such as `Parameters.xml` and `Switches.xml`, which contain configuration parameters read by this helper.

This helper is part of the [Helpers](../Helpers) namespace in the MixERP.Net.Common assembly, which contains other utility classes like [DateHelper.cs](DateHelper.md), [ExpressionHelper.cs](ExpressionHelper.md), and [Parameters.cs](Parameters.md).

## Related Files

- [Parameters.cs](Parameters.md) - Likely uses this helper to access specific parameter configurations
- [Switches.cs](Switches.md) - May use this helper to access feature switch configurations