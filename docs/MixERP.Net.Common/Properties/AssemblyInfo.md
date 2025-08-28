# AssemblyInfo.cs Documentation

## Overview

This file contains assembly attributes that define metadata for the `MixERP.Net.Common` assembly. Assembly attributes provide information about an assembly, such as its name, description, version, and other properties that can be queried programmatically at runtime. This particular file configures important assembly-level attributes for the MixERP.Net.Common library, which serves as a common utilities and models library for the MixERP application framework.

## Assembly Attributes Documentation

### General Information Attributes

These attributes define basic information about the assembly:

- **AssemblyTitle**: "MixERP.Net.Common"
  - Specifies the display name of the assembly.

- **AssemblyDescription**: ""
  - Provides a description of the assembly's functionality (currently empty).

- **AssemblyConfiguration**: ""
  - Specifies the build configuration (e.g., Debug or Release) used for this assembly (currently empty).

- **AssemblyCompany**: ""
  - Identifies the company that produced the assembly (currently empty).

- **AssemblyProduct**: "MixERP.Net.Common"
  - Specifies the product name of which the assembly is a part.

- **AssemblyCopyright**: "Copyright © 2013"
  - Specifies copyright information for the assembly.

- **AssemblyTrademark**: ""
  - Specifies trademark information for the assembly (currently empty).

- **AssemblyCulture**: ""
  - Specifies the culture supported by the assembly (currently empty, indicating culture-neutral).

- **CLSCompliant**: true
  - Indicates that this assembly follows the Common Language Specification (CLS) compliance requirements, ensuring it can be used by any .NET language.

### COM Interoperability Attributes

These attributes define how the assembly interacts with COM components:

- **ComVisible**: false
  - When set to false, types in this assembly are not accessible to COM components. This is the default setting for .NET assemblies for security and simplicity.

- **Guid**: "d97d61cb-d3d4-4936-93c9-67e7b3af1ee9"
  - A unique identifier that represents the typelib if this assembly is exposed to COM.

### Version Information Attributes

These attributes define version information for the assembly:

- **AssemblyVersion**: "1.0.0.0"
  - Specifies the version of the assembly in the format `Major.Minor.Build.Revision`.

- **AssemblyFileVersion**: "1.0.0.0"
  - Specifies the version number used for the Win32 file version resource.

## Related Files

The `MixERP.Net.Common` assembly contains various helper classes and models that support the MixERP application framework:

- Helper classes:
  - [ConfigurationHelper.cs](../MixERP.Net.Common/Helpers/ConfigurationHelper.md)
  - [DateHelper.cs](../MixERP.Net.Common/Helpers/DateHelper.md)
  - [ExpressionHelper.cs](../MixERP.Net.Common/Helpers/ExpressionHelper.md)
  - [LocalizationHelper.cs](../MixERP.Net.Common/Helpers/LocalizationHelper.md)
  - [Parameters.cs](../MixERP.Net.Common/Helpers/Parameters.md)
  - [Switches.cs](../MixERP.Net.Common/Helpers/Switches.md)

- Core models:
  - [Menus.cs](../MixERP.Net.Common/Models/Core/Menus.md)
  - [ProductControlModel.cs](../MixERP.Net.Common/Models/Core/ProductControlModel.md)

- Transaction models:
  - [JournalDetailsModel.cs](../MixERP.Net.Common/Models/Transactions/JournalDetailsModel.md)
  - [ProductDetailsModel.cs](../MixERP.Net.Common/Models/Transactions/ProductDetailsModel.md)
  - [ProductModel.cs](../MixERP.Net.Common/Models/Transactions/ProductModel.md)

- Utility classes:
  - [Conversion.cs](../MixERP.Net.Common/Conversion.md)
  - [ExceptionManager.cs](../MixERP.Net.Common/ExceptionManager.md)
  - [PageUtility.cs](../MixERP.Net.Common/PageUtility.md)

## Usage

Assembly attributes are typically not accessed directly in code but are used by the .NET runtime and tools to obtain information about an assembly. They can be accessed programmatically using reflection if needed:

```csharp
// Example of accessing assembly information at runtime
Assembly assembly = typeof(SomeTypeInTheAssembly).Assembly;
string title = assembly.GetCustomAttribute<AssemblyTitleAttribute>()?.Title;
string version = assembly.GetName().Version.ToString();
```

## License Information

This file is part of the MixERP project and is subject to the Mozilla Public License, v. 2.0. The license header at the top of the file indicates that this code is copyrighted by Binod Nepal, Mix Open Foundation (http://mixof.org).