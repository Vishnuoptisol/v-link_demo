# MixERP.Net.FrontEnd.licenseheader

## Overview

The `MixERP.Net.FrontEnd.licenseheader` file defines standardized license headers for various file types in the MixERP.Net.FrontEnd project. This file ensures that all source code files contain proper copyright and licensing information, which is crucial for open-source software distribution. The license used is the Mozilla Public License v. 2.0 (MPL-2.0), and the copyright is attributed to Binod Nepal and the Mix Open Foundation.

## File Structure Documentation

### License Header Configuration

The file configures license headers for different file extensions using the following format:

#### For C#, C++, and H files
```csharp
/********************************************************************************
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
***********************************************************************************/
```

#### For ASPX, ASCX, and Master files
```html
<%-- 
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
--%>
```

#### For VB files
```vb
'Sample license text.
```

#### For XML, Config, and XSD files
```xml
<!--
Copyright (C) Binod Nepal, Mix Open Foundation (http://mixof.org).

This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. 
If a copy of the MPL was not distributed with this file, You can obtain one at 
http://mozilla.org/MPL/2.0/.
-->
```

## Usage in the Project

This file is used by the Visual Studio IDE to automatically insert the appropriate license header when creating new files or when explicitly applying the header to existing files. The license header applies to a wide range of files in the MixERP.Net.FrontEnd project, including:

1. C# files (`.cs`) - Used for backend code and business logic
2. ASP.NET files (`.aspx`, `.ascx`) - Used for web forms and user controls
3. Master pages (`.Master`) - Used for page templates
4. XML and configuration files (`.xml`, `.config`, `.xsd`) - Used for settings and data structures

## Mozilla Public License (MPL-2.0)

The Mozilla Public License v. 2.0 is a weak copyleft license that allows integration of MPL-licensed code with proprietary software, provided that the MPL-licensed portions remain under the MPL. Key points about MPL-2.0:

1. It requires that source code modifications be available under the MPL
2. It allows linking to code under different licenses
3. It provides patent rights
4. It requires attribution to the original author

## Related Files

This license header is applied to numerous files throughout the MixERP.Net.FrontEnd project, including:

- [Global.asax.cs](Global.asax.cs.md) - Application startup and configuration
- [MixERPMaster.Master](MixERPMaster.Master.md) - Main master page template
- [Web.config](Web.config.md) - Main application configuration

## Best Practices

When working with the MixERP.Net.FrontEnd project, developers should:

1. Ensure all new files have the appropriate license header
2. Maintain the existing license information when modifying files
3. Check that the license header format is correct for each file type
4. Not remove or alter license headers without proper authorization

## References

1. [Mozilla Public License v. 2.0](http://mozilla.org/MPL/2.0/)
2. [Mix Open Foundation](http://mixof.org)