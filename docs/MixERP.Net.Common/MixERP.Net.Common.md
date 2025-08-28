# MixERP.Net.Common.licenseheader Documentation

## Overview

`MixERP.Net.Common.licenseheader` defines the standard license header text that is applied to source code files throughout the MixERP project. This file contains the Mozilla Public License v2.0 text templates for different file types, ensuring consistent license attribution across the codebase.

## License Header Templates

### C# and C++ Files (.cs, .cpp, .h)

The file defines the license header for C#, C++ source and header files with the following text:

```csharp
/********************************************************************************
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
***********************************************************************************/
```

### ASP.NET Files (.aspx, .ascx)

For ASP.NET web form and user control files, the license is formatted as an HTML comment:

```aspx
<%-- 
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
--%>
```

### Visual Basic Files (.vb)

A placeholder for VB files is included:

```vb
'Sample license text.
```

### XML and Configuration Files (.xml, .config, .xsd)

For XML-based files, the license is formatted as an XML comment:

```xml
<!--
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
-->
```

## Usage

This license header file is used by Visual Studio and other development tools to automatically add the appropriate license text to the top of new files or existing files in the MixERP project. It ensures that all code files maintain proper copyright and license information.

The license header applies to various components of the MixERP.Net project, including:

- Common libraries in [MixERP.Net.Common](./MixERP.Net.Common.md)
- Helper classes like those found in the [Helpers](./Helpers/ConfigurationHelper.md) namespace
- Model classes in [Models](./Models/Core/Menus.md) namespace

## License Information

The MixERP project is licensed under the Mozilla Public License v2.0, which allows for the code to be used, modified, and distributed, with certain conditions regarding source code distribution and notification requirements.

The license headers indicate that copyright is held by Binod Nepal and the Mix Open Foundation (http://mixof.org).

## Related Files

This license header is applied to various files throughout the project, including:

- [ConfigurationHelper.cs](./Helpers/ConfigurationHelper.md)
- [DateHelper.cs](./Helpers/DateHelper.md)
- [ExpressionHelper.cs](./Helpers/ExpressionHelper.md)
- [Conversion.cs](./Conversion.md)
- [ExceptionManager.cs](./ExceptionManager.md)
- [PageUtility.cs](./PageUtility.md)