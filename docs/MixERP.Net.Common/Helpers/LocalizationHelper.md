# LocalizationHelper.cs Documentation

## Overview

The `LocalizationHelper` class provides utility methods for retrieving localized resources in the MixERP application. This static helper class facilitates resource string retrieval from global resources based on a specified class name and key, with support for culture-specific localization.

## Class Documentation

### LocalizationHelper

**Namespace:** `MixERP.Net.Common.Helpers`  
**Type:** Static class  
**Access Modifier:** Public  

A static utility class that provides methods to access and retrieve localized strings from resource files.

## Method Documentation

### GetResourceString(string className, string key)

**Access Modifier:** Public  
**Return Type:** `string`  
**Parameters:**
- `className` (string): The name of the resource class to retrieve resources from
- `key` (string): The specific resource key to look up

**Description:**  
Retrieves a localized resource string from the global resource file based on the specified class name and key. This method will throw an exception if the resource cannot be found.

**Steps:**
1. Checks if the provided key is null/empty or if there's no current HttpContext
2. If validation passes, attempts to retrieve the resource using the current culture
3. If the resource cannot be found, throws an InvalidOperationException

**Example Usage:**
```csharp
string localizedLabel = LocalizationHelper.GetResourceString("Labels", "Welcome");
```

**Exceptions:**
- `InvalidOperationException`: Thrown when the specified resource cannot be found

### GetResourceString(string className, string key, bool throwError)

**Access Modifier:** Public  
**Return Type:** `string`  
**Parameters:**
- `className` (string): The name of the resource class to retrieve resources from
- `key` (string): The specific resource key to look up
- `throwError` (bool): Determines whether to throw an exception if the resource is not found

**Description:**  
An overloaded version of GetResourceString that allows control over exception handling. When `throwError` is set to false, the method will return the key itself instead of throwing an exception when a resource is not found.

**Steps:**
1. Checks if the provided key is null/empty or if there's no current HttpContext
2. If validation passes, attempts to retrieve the resource using the current culture
3. If the resource cannot be found and `throwError` is true, throws an InvalidOperationException
4. If the resource cannot be found and `throwError` is false, returns the key as the fallback

**Example Usage:**
```csharp
// Won't throw an exception if resource not found, will return "CustomerName" instead
string labelText = LocalizationHelper.GetResourceString("Labels", "CustomerName", false);
```

**Exceptions:**
- `InvalidOperationException`: Thrown when the specified resource cannot be found and `throwError` is set to true

### Culture()

**Access Modifier:** Public  
**Return Type:** `CultureInfo`  
**Parameters:** None

**Description:**  
Returns a CultureInfo object representing the current culture to be used for localization. Currently, this method is marked as "Todo" and returns an invariant culture, indicating it's likely a placeholder for future implementation that would return the user's current culture.

**Steps:**
1. Creates a new CultureInfo object using the InvariantCulture's name
2. Returns the created culture object

**Example Usage:**
```csharp
CultureInfo currentCulture = LocalizationHelper.Culture();
```

## Related Files

This class has dependencies on the following system components:
- `System.Globalization.CultureInfo`
- `System.Web.HttpContext`

It is used by various parts of the MixERP application for internationalization and localization purposes.

## Notes

The `Culture()` method is marked with a "Todo" comment, indicating that the current implementation (returning invariant culture) is temporary. A future implementation would likely determine the appropriate culture based on user preferences or browser settings.