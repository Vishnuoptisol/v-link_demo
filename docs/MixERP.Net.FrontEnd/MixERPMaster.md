# MixERPMaster.Master Documentation

## Overview

`MixERPMaster.Master` serves as the primary master page template for the MixERP application's frontend. It defines the basic HTML structure, common JavaScript libraries, CSS stylesheets, and layout that will be inherited by pages throughout the application. The master page includes the header with logo, navigation menu, content area, and footer, providing a consistent user interface across the application.

## Structure Documentation

### Master Page Definition

```csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="MixErpMaster.Master.cs" 
    Inherits="MixERP.Net.FrontEnd.MixErpMaster" %>
```

This directive defines a master page written in C# that automatically wires up events at page load. The code-behind file is [MixERPMaster.Master.cs](MixERPMaster.Master.cs), and the class inherits from `MixErpMaster` in the `MixERP.Net.FrontEnd` namespace.

### HTML Structure

The master page defines a complete HTML document structure with:
- HTML5 doctype declaration
- Head section containing CSS and JavaScript references
- Body containing the main layout structure
- Content placeholder regions for child pages to populate

### Content PlaceHolders

1. **ScriptContentPlaceHolder**: For page-specific JavaScript includes in the head section
2. **StyleSheetContentPlaceHolder**: For page-specific CSS styles in the head section
3. **BodyContentPlaceHolder**: The main content area where child pages render their content
4. **BottomScriptContentPlaceHolder**: For page-specific JavaScript that should be executed after the page loads

### CSS References

```html
<link href="~/themes/purple/main.css" rel="stylesheet" type="text/css" runat="server" />
<link href="/Scripts/colorbox/colorbox.css" rel="stylesheet" />
```

The master page references the main theme stylesheet from [/themes/purple/main.css](Themes/purple/main.css) and the ColorBox plugin's CSS for modal dialogs.

### JavaScript Libraries

The page includes several JavaScript libraries:

1. **jQuery**: Core JavaScript library for DOM manipulation and AJAX
   ```html
   <script src="/Scripts/jquery.min.js" type="text/javascript"></script>
   ```

2. **Shortcut.js**: For keyboard shortcut handling
   ```html
   <script src="/Scripts/shortcut.js"></script>
   ```

3. **ColorBox**: jQuery plugin for lightbox/modal windows
   ```html
   <script src="/Scripts/colorbox/jquery.colorbox-min.js"></script>
   ```

4. **jQuery Number**: For number formatting
   ```html
   <script src="/Scripts/jqueryNumber/jquery.number.min.js"></script>
   ```

5. **Date.js**: For date manipulation
   ```html
   <script src="/Scripts/date.js"></script>
   ```

6. **Chart.js**: For data visualization
   ```html
   <script src="/Scripts/chartjs/Chart.min.js"></script>
   <script src="/Scripts/chartjs/legend.js"></script>
   ```

7. **MixERP.js**: Application-specific JavaScript
   ```html
   <script src="/Scripts/mixerp.js" type="text/javascript"></script>
   ```

### Global JavaScript Variables

The master page defines several global JavaScript variables that are populated from server-side code:

```javascript
var today = "<%= System.DateTime.Now.ToShortDateString() %>";
var shortDateFormat = "<%= MixERP.Net.Common.Helpers.Parameters.ShortDateFormat() %>";
var thousandSeparator = "<%= MixERP.Net.Common.Helpers.Parameters.ThousandSeparator() %>";
var decimalSeparator = "<%= MixERP.Net.Common.Helpers.Parameters.DecimalSeparator() %>";
var decimalPlaces = "<%= MixERP.Net.Common.Helpers.Parameters.DecimalPlaces() %>";
```

These variables store localization information for dates and number formatting, making them available to all JavaScript code on the page.

### Page Layout

The page layout consists of:

1. **Logo/Header**: Application logo linking to the dashboard
   ```html
   <a href="/Dashboard/Index.aspx">
       <img src="/themes/purple/mixerp-logo.png" height="50" width="250" />
   </a>
   ```

2. **Menu**: Navigation menu and user account actions
   ```html
   <div id="menu">
       <asp:Literal ID="MenuLiteral" runat="server" />
       <div style="float: right;">
           <a href="/Account/SignOut.aspx" class="icon">
               <img src="/Resource/Icons/signout-16.png" />
           </a>
           <a href="/Account/ChangePassword.aspx" class="icon">
               <img src="/Resource/Icons/password-16.png" />
           </a>
       </div>
   </div>
   ```

   The menu includes links to:
   - [SignOut.aspx](Account/SignOut.aspx) - For user logout
   - [ChangePassword.aspx](Account/ChangePassword.aspx) - For password management

3. **Content Area**: Where page-specific content is rendered
   ```html
   <div id="content">
       <asp:ContentPlaceHolder ID="BodyContentPlaceHolder" runat="server">
       </asp:ContentPlaceHolder>
       <asp:Button ID="SwallowSubmitButton" runat="server" OnClientClick="return(false);" Style="display: none;" />
   </div>
   ```

4. **Footer**: Copyright and application information
   ```html
   <div id="footer">
       Powered by
       <a href="http://MixERP.Net" target="_blank">MixErp® Beta</a>
   </div>
   ```

### Client-Side Features

1. **Form Definition**:
   ```html
   <form id="form1" runat="server" enctype="multipart/form-data" method="post" submitdisabledcontrols="true" defaultbutton="SwallowSubmitButton">
   ```
   - Configured to support file uploads (`enctype="multipart/form-data"`)
   - Submits disabled controls (`submitdisabledcontrols="true"`)
   - Uses a hidden default button to prevent accidental form submissions when pressing Enter

2. **Print Prevention**:
   ```javascript
   jQuery(document).bind("keyup keydown", function (e) {
       if (e.ctrlKey && e.keyCode == 80) {
           event.preventDefault();
           return false;
       }
   });
   ```
   Prevents the browser's print dialog (Ctrl+P) from opening.

3. **ColorBox Initialization**:
   ```javascript
   function pageLoad(sender, args) {
       $(".item-selector").colorbox({ iframe: true, innerWidth: 1024, innerHeight: 450, overlayClose: false });
       $(".preview").colorbox({ iframe: true, innerWidth: 1024, innerHeight: 450, overlayClose: false });
   }
   ```
   Initializes ColorBox modal windows for elements with classes "item-selector" and "preview".

## Server-Side Code Usage

The master page makes use of server-side code in several places:

1. **Date and Number Format Parameters**:
   ```csharp
   MixERP.Net.Common.Helpers.Parameters.ShortDateFormat()
   MixERP.Net.Common.Helpers.Parameters.ThousandSeparator()
   MixERP.Net.Common.Helpers.Parameters.DecimalSeparator()
   MixERP.Net.Common.Helpers.Parameters.DecimalPlaces()
   ```
   These methods retrieve localization parameters from application settings.

2. **Menu Generation**:
   ```html
   <asp:Literal ID="MenuLiteral" runat="server" />
   ```
   This literal control is populated in the [code-behind](MixERPMaster.Master.cs) to render the dynamic navigation menu.

## Browser Compatibility

The master page includes specific CSS adjustments for Internet Explorer:

```html
<!--[if IE]>
    <style>
    .grid3 td
    {
        padding-left:1px!important;
    }
    </style>
<![endif]-->
```

This conditional comment applies specific padding to table cells in grid elements when viewed in Internet Explorer.

## Dependencies

This master page depends on the following other files within the project:

1. Code-behind file: [MixERPMaster.Master.cs](MixERPMaster.Master.cs)
2. CSS files:
   - [/themes/purple/main.css](Themes/purple/main.css)
   - [/Scripts/colorbox/colorbox.css](Scripts/colorbox/colorbox.css)
3. JavaScript files:
   - [/Scripts/jquery.min.js](Scripts/jquery.min.js)
   - [/Scripts/shortcut.js](Scripts/shortcut.js)
   - [/Scripts/colorbox/jquery.colorbox-min.js](Scripts/colorbox/jquery.colorbox-min.js)
   - [/Scripts/jqueryNumber/jquery.number.min.js](Scripts/jqueryNumber/jquery.number.min.js)
   - [/Scripts/date.js](Scripts/date.js)
   - [/Scripts/chartjs/Chart.min.js](Scripts/chartjs/Chart.min.js)
   - [/Scripts/chartjs/legend.js](Scripts/chartjs/legend.js)
   - [/Scripts/mixerp.js](Scripts/mixerp.js)
4. Related pages:
   - [/Dashboard/Index.aspx](Dashboard/Index.aspx)
   - [/Account/SignOut.aspx](Account/SignOut.aspx)
   - [/Account/ChangePassword.aspx](Account/ChangePassword.aspx)

## Usage

To use this master page in a content page:

```
<%@ Page Language="C#" MasterPageFile="~/MixERPMaster.Master" AutoEventWireup="true" 
    CodeBehind="YourPage.aspx.cs" Inherits="MixERP.Net.FrontEnd.YourNamespace.YourPage" %>

<asp:Content ID="Content1" ContentPlaceHolderID="ScriptContentPlaceHolder" runat="server">
    <!-- Page-specific scripts -->
</asp:Content>

<asp:Content ID="Content2" ContentPlaceHolderID="StyleSheetContentPlaceHolder" runat="server">
    <!-- Page-specific styles -->
</asp:Content>

<asp:Content ID="Content3" ContentPlaceHolderID="BodyContentPlaceHolder" runat="server">
    <!-- Page content -->
</asp:Content>

<asp:Content ID="Content4" ContentPlaceHolderID="BottomScriptContentPlaceHolder" runat="server">
    <!-- Scripts to run after page loads -->
</asp:Content>
```