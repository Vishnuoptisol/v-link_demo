# RuntimeError.aspx Documentation

## Overview
`RuntimeError.aspx` is an ASP.NET Web Form that serves as an error page in the MixERP.Net.FrontEnd application. It displays a user-friendly error message when runtime exceptions occur during application execution. The page inherits from the [ContentMaster.Master](ContentMaster.Master.md) master page to maintain consistent layout and styling across the application.

## File Structure
The file is structured as a standard ASP.NET Web Form with content placeholders defined by the master page:
- `ScriptContentPlaceHolder` - For JavaScript scripts
- `StyleSheetContentPlaceHolder` - For CSS stylesheets
- `BodyContentPlaceHolder` - For the main body content (error message and details)
- `BottomScriptContentPlaceHolder` - For scripts that need to be placed at the bottom of the page

## Page Content
The page displays:
1. A heading "Error Occurred"
2. A horizontal rule separator
3. A friendly message explaining that an error has occurred
4. A suggestion to notify the project administrator for serious errors
5. The actual exception details (rendered via a Literal control)
6. A link to return to the previous page

## Server Controls

### ExceptionLiteral
- **Type**: `asp:Literal`
- **ID**: `ExceptionLiteral`
- **Purpose**: Displays the exception details that are populated from the code-behind file [RuntimeError.aspx.cs](RuntimeError.aspx.cs.md)
- **Attributes**:
  - `runat="server"` - Indicates that this control is processed on the server side

## Navigation
The page provides a "Go Back to the Previous Page" link that uses JavaScript's `history.go(-1)` method to navigate the user back to the previous page they were on before the error occurred.

## Dependencies
1. **Master Page**: 
   - [ContentMaster.Master](ContentMaster.Master.md) - Provides the layout structure for this page
2. **Code-Behind File**:
   - [RuntimeError.aspx.cs](RuntimeError.aspx.cs.md) - Contains the server-side logic for the page
   - [RuntimeError.aspx.designer.cs](RuntimeError.aspx.designer.cs.md) - Contains the designer-generated code for the page controls

## Styling
The page uses:
- The default styling provided by the master page
- A CSS class named "hr" for the horizontal rule
- A CSS class named "menu" for the "Go Back" link styling

## Functionality
When an unhandled exception occurs in the application:
1. The user is redirected to this page
2. The exception details are captured by the code-behind file
3. The details are displayed in the `ExceptionLiteral` control
4. The user is given options to go back or contact the administrator

## License Information
The page is licensed under the Mozilla Public License, v. 2.0, as indicated in the header comments. The copyright is attributed to Binod Nepal, Mix Open Foundation (http://mixof.org).