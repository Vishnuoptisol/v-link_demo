# Global.asax Documentation

## Overview

The `Global.asax` file serves as the application entry point for the MixERP.Net.FrontEnd web application. It is an ASP.NET specific file that declares the Global application class, which is defined in the corresponding code-behind file [Global.asax.cs](Global.asax.cs.md). This file is automatically processed by the ASP.NET runtime during application startup.

## File Structure

This file is a standard ASP.NET application directive file with the following characteristics:

- **File Type**: ASP.NET Application File
- **Language**: C#
- **Codebehind**: [Global.asax.cs](Global.asax.cs.md) - Contains the actual implementation of the Global class
- **Inherits**: MixERP.Net.FrontEnd.Global - The class that this file inherits from, defined in the codebehind

## Functionality

The `Global.asax` file doesn't contain any direct functionality itself, but rather serves as a declaration that connects the ASP.NET runtime to the Global class defined in [Global.asax.cs](Global.asax.cs.md). The Global class typically contains:

1. Application initialization code
2. Session state management
3. Error handling
4. Application-wide event handling

These functionalities are implemented in the [Global.asax.cs](Global.asax.cs.md) file, which contains the actual C# code that runs during the application lifecycle events.

## Application Events

Through its connection to the Global class, this file enables the handling of various ASP.NET application events:

- Application_Start: Fired when the application starts
- Application_End: Fired when the application ends
- Session_Start: Fired when a new user session begins
- Session_End: Fired when a user session times out or ends
- Application_Error: Fired when an unhandled exception occurs

The implementation details of these event handlers can be found in the [Global.asax.cs](Global.asax.cs.md) file.

## Related Files

- [Global.asax.cs](Global.asax.cs.md): Contains the actual C# implementation of the Global class
- [Web.config](Web.config.md): Contains application configuration settings that may be used by code in Global.asax.cs

## Usage

This file is automatically used by the ASP.NET runtime and doesn't need to be directly referenced in code. The ASP.NET runtime automatically processes this file during application startup to establish the application-level event handling and initialization.