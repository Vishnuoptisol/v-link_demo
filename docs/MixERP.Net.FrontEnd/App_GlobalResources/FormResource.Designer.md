# FormResource.Designer.cs Documentation

## Overview

`FormResource.Designer.cs` is an auto-generated resource class file that provides strongly-typed access to localized strings within the MixERP.Net application. This class serves as a centralized repository for form-related labels, field names, and other UI text elements used throughout the application. The auto-generated nature of this file means that it's maintained by tools like Visual Studio's Resource Designer or ResGen, and manual changes should be avoided as they will be overwritten during code regeneration.

The class is part of the `Resources` namespace and is designed to make localization and internationalization more manageable by providing programmatic access to resource strings through strongly-typed properties rather than loose string literals.

## Class Documentation

### FormResource

**Namespace**: `Resources`  
**Access Modifier**: `internal`  
**Type**: Auto-generated resource class  
**Purpose**: Provides strongly-typed access to localized strings for form elements.

#### Attributes

- **Static ResourceManager**: Manages access to the culture-specific resources.
- **Static CultureInfo**: Represents the culture for which the resource manager returns resources.

#### Constructors

- **FormResource()**: Default constructor, marked with `SuppressMessage` to avoid compiler warnings about uncalled private code.

#### Properties

The class contains over 350 static properties, each representing a localized string resource. Each property:
- Is defined as `internal static string`
- Follows a snake_case naming convention
- Has an XML documentation summary describing the text it represents
- Returns the string from the ResourceManager using the property name as the key and the current culture

Here are some examples of the properties provided:

| Property Name | Description | Sample Value |
|---------------|-------------|--------------|
| account_code | Label for account code fields | "Account Code" |
| account_name | Label for account name fields | "Account Name" |
| address | Label for address fields | "Address" |
| amount | Label for amount fields | "Amount" |
| description | Label for description fields | "Description" |
| email | Label for email fields | "Email" |
| office_id | Label for office ID fields | "Office Id" |
| party_name | Label for party name fields | "Party Name" |
| price | Label for price fields | "Price" |
| quantity | Label for quantity fields | "Quantity" |
| tax_rate | Label for tax rate fields | "Tax Rate" |
| user_name | Label for user name fields | "User Name" |

## Method Documentation

### ResourceManager

**Access Modifier**: `internal static`  
**Return Type**: `global::System.Resources.ResourceManager`  
**Purpose**: Returns the cached ResourceManager instance used by the class.

**Steps**:
1. Check if the `resourceMan` field is null
2. If null, create a new ResourceManager for "Resources.FormResource" in the App_GlobalResources assembly
3. Assign the new ResourceManager to the `resourceMan` field
4. Return the ResourceManager instance

**Example Usage**:
```csharp
var manager = FormResource.ResourceManager;
string localizedString = manager.GetString("account_code", someCulture);
```

### Culture

**Access Modifier**: `internal static`  
**Return Type**: `global::System.Globalization.CultureInfo`  
**Purpose**: Gets or sets the culture info used for resource lookups.

**Example Usage**:
```csharp
// Change the culture for all subsequent resource lookups
FormResource.Culture = new System.Globalization.CultureInfo("es-ES");

// Get the current culture
var currentCulture = FormResource.Culture;
```

## API Documentation

This file doesn't define any API endpoints as it's a resource class designed for internal use within the application to provide localized strings.

## Usage Notes

1. **Localization**: This resource file is paired with a corresponding `.resx` file (`FormResource.resx` located in the App_GlobalResources directory) that contains the actual string resources. To add support for additional languages, you would create culture-specific resource files (e.g., `FormResource.es-ES.resx`).

2. **Modification**: Any direct changes to this file will be lost when it's regenerated. To add or modify resources, you should use the resource editor in Visual Studio to edit the corresponding `.resx` file.

3. **Integration**: This resource class is typically used across the application's UI components to ensure consistent terminology and enable localization without hardcoding strings in the UI code.

4. **Related Files**: This class works together with other resource files in the `App_GlobalResources` directory including:
   - [Labels.resx](MixERP.Net.FrontEnd/App_GlobalResources/Labels.resx)
   - [Questions.resx](MixERP.Net.FrontEnd/App_GlobalResources/Questions.resx)
   - [Setup.resx](MixERP.Net.FrontEnd/App_GlobalResources/Setup.resx)
   - [Titles.resx](MixERP.Net.FrontEnd/App_GlobalResources/Titles.resx)
   - [Warnings.resx](MixERP.Net.FrontEnd/App_GlobalResources/Warnings.resx)