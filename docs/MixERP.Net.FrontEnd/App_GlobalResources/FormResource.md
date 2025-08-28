# FormResource.resx Documentation

## Overview

`FormResource.resx` is a resource file in the MixERP.Net.FrontEnd project that contains localized string resources for form labels and field names. This file is part of the application's globalization framework, providing a centralized repository of UI text that can be easily translated and maintained. The file follows the standard .NET Resource (.resx) format which stores string resources in XML format, allowing for language-specific text to be loaded at runtime based on the user's culture settings.

## Resource File Documentation

### Purpose

The primary purpose of this resource file is to define display names and labels for form fields across the MixERP application. These resources are referenced in the application's UI components, making it possible to display localized field names without hardcoding strings in the application's code.

### Structure

The file follows the standard .NET Resource (.resx) format with the following components:

- XML header with schema definitions
- Resource header information specifying MIME type, version, and resource handlers
- Data elements containing the string resources, each with a unique name and value

### Resource Headers

The resource file contains standard .NET resource headers:

```xml
<resheader name="resmimetype">
  <value>text/microsoft-resx</value>
</resheader>
<resheader name="version">
  <value>2.0</value>
</resheader>
<resheader name="reader">
  <value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<resheader name="writer">
  <value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
```

### Related Files

This resource file works together with its designer file:

- [FormResource.Designer.cs](FormResource.Designer.cs.md) - Auto-generated code providing strongly-typed access to the resources

## Resource Entries

The file contains over 300 string resources representing various form elements and labels used throughout the MixERP application. These resources are organized alphabetically and follow a naming convention where the name represents the data field or property it describes.

### Key Resource Categories

The resources can be broadly categorized into the following groups:

1. **General Entity Identifiers**
   - account_id, customer_id, item_id, office_id, etc.

2. **Account & Financial Fields**
   - account_name, bank_account_code, currency_code, etc.

3. **User & Authentication Fields**
   - user_id, user_name, password, etc.

4. **Party Information Fields**
   - party_name, party_code, party_type, etc.

5. **Item & Inventory Fields**
   - item_code, item_name, quantity, etc.

6. **Tax & Pricing Fields**
   - tax_code, tax_amount, price, etc.

7. **Contact Information Fields**
   - address, phone, email, city, etc.

8. **Metadata & System Fields**
   - audit_ts, transaction_ts, status, etc.

### Usage Examples

These resources are typically used in ASP.NET controls, such as in form labels, grid headers, and validation messages. They're accessed through the auto-generated designer class in code, for example:

```csharp
// Setting a label text
lblItemCode.Text = FormResource.item_code;

// Setting a column header
gridColumn.HeaderText = FormResource.item_name;
```

In ASP.NET pages, they might be referenced as:

```html
<asp:Label ID="lblAccountCode" runat="server" Text="<%$ Resources:FormResource, account_code %>"></asp:Label>
```

## Key Resource Entries

Below is a sample of the most commonly used resources in the file:

| Resource Name | Value | Used In |
|---------------|-------|---------|
| account_code | Account Code | Financial forms, account setup |
| account_name | Account Name | Financial forms, account setup |
| address | Address | Party forms, office setup |
| amount | Amount | Transaction forms |
| customer_name | Customer Name | Sales forms |
| description | Description | Various entity forms |
| email | Email | Contact information forms |
| item_code | Item Code | Inventory forms |
| item_name | Item Name | Inventory forms |
| office_code | Office Code | Office setup forms |
| party_name | Party Name | Customer/Supplier forms |
| price | Price | Sales and purchase forms |
| quantity | Quantity | Inventory and transaction forms |
| tax | Tax | Sales and purchase forms |
| total | Total | Transaction forms |
| user_name | User Name | User management forms |

## Dependencies

This resource file is used across many forms and controls in the MixERP application. Some of the key files that may reference these resources include:

- [UserControls/Forms/FormControl.ascx](../UserControls/Forms/FormControl.ascx.md)
- [Items/Setup/Items.aspx](../Items/Setup/Items.aspx.md)
- [Finance/Setup/COA.aspx](../Finance/Setup/COA.aspx.md)
- [Setup/Users.aspx](../Setup/Users.aspx.md)
- [Items/Setup/Parties.aspx](../Items/Setup/Parties.aspx.md)

## Implementation Notes

1. When adding new forms or fields to the MixERP application, corresponding entries should be added to this resource file to support localization.

2. The resource file is used in conjunction with other language-specific resource files to provide multilingual support.

3. The auto-generated `FormResource.Designer.cs` file provides strongly-typed access to these resources, offering compile-time checking and IntelliSense support.

4. This file primarily contains English (default) language resources. For other languages, separate culture-specific resource files should be created following the naming convention `FormResource.{culture-code}.resx`.