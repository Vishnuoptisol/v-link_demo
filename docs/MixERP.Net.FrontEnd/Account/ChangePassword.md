# ChangePassword.aspx Documentation

## Overview

The `ChangePassword.aspx` file is a web page in the MixERP.Net.FrontEnd application that provides users with the functionality to change their account passwords. It is part of the Account management section of the MixERP application. The page uses the ContentMaster.Master master page for its layout and structure.

## File Structure

This ASP.NET Web Form is structured with four content placeholders:

1. **ScriptContentPlaceHolder** - For JavaScript code
2. **StyleSheetContentPlaceHolder** - For CSS stylesheets
3. **BodyContentPlaceHolder** - For the main content of the page
4. **BottomScriptContentPlaceHolder** - For scripts that need to be loaded at the bottom of the page

Currently, all content placeholders are empty, indicating that the actual implementation of the password change functionality is likely handled in the code-behind file (`ChangePassword.aspx.cs`).

## Dependencies

- **Master Page**: Uses [`ContentMaster.Master`](../ContentMaster.Master.md) for the page layout
- **Code-Behind**: Inherits from `MixERP.Net.FrontEnd.Account.ChangePassword` which is defined in [`ChangePassword.aspx.cs`](ChangePassword.aspx.cs.md)

## Page Details

- **Title**: Not specified (empty string)
- **Language**: C#
- **AutoEventWireup**: true
- **Inheritance**: Inherits from `MixERP.Net.FrontEnd.Account.ChangePassword`

## Licensing

The file includes the Mozilla Public License v2.0 copyright notice, indicating that it is open-source software maintained by Binod Nepal and the Mix Open Foundation (http://mixof.org).

## Notes

The page appears to be a template or placeholder waiting for implementation. While the structure for a password change form exists, the actual form elements, validation controls, and submission logic would need to be implemented in the `BodyContentPlaceHolder` and the code-behind file.

This page would typically include:
- Password input fields (current password, new password, confirm new password)
- Validation controls to ensure password requirements are met
- A submit button to process the password change
- Possibly feedback messages or alerts for success/failure

Since the content sections are empty, users would currently not be able to interact with this page in any meaningful way until the implementation is completed.