# ContentMaster.Master Documentation

## Overview

`ContentMaster.Master` is a nested master page in the MixERP.Net.FrontEnd application that provides a structured layout template for content pages. It inherits from [MixERPMaster.Master](MixERPMaster.Master.md) and adds a two-column layout consisting of a menu column and a content column. This master page defines placeholders for scripts, stylesheets, and the main body content, allowing child pages to inject their specific content while maintaining a consistent application layout.

## Master Page Documentation

### ContentMaster

This master page creates a structured layout with a menu panel on the left side and content area on the right.

#### Inheritance

- Inherits from: [MixERPMaster.Master](MixERPMaster.Master.md)
- Code-behind: [ContentMaster.Master.cs](ContentMaster.Master.cs.md)
- Designer: [ContentMaster.Master.designer.cs](ContentMaster.Master.designer.cs.md)

#### Content Placeholders

The master page defines several content placeholders that are populated by its child pages:

1. **ScriptContentPlaceHolder**
   - Type: `asp:ContentPlaceHolder`
   - Purpose: Contains JavaScript code that needs to be loaded in the head section of the page

2. **StyleSheetContentPlaceHolder**
   - Type: `asp:ContentPlaceHolder`
   - Purpose: Contains CSS styles that need to be loaded in the head section of the page

3. **BodyContentPlaceHolder**
   - Type: `asp:ContentPlaceHolder`
   - Purpose: Contains the main content of the page

4. **BottomScriptContentPlaceHolder**
   - Type: `asp:ContentPlaceHolder`
   - Purpose: Contains JavaScript code that needs to be loaded at the bottom of the page

#### Controls

1. **SearchTextBox**
   - Type: `asp:TextBox`
   - ID: `SearchTextBox`
   - Purpose: Provides a search functionality in the menu panel

2. **ContentMenuLiteral**
   - Type: `asp:Literal`
   - ID: `ContentMenuLiteral`
   - Purpose: Dynamically populated with menu items in the code-behind file

#### Layout Structure

The layout is organized in a table with two columns:
- Left column (class "menu2"): Contains the search textbox and navigation menu
- Right column: Contains the main content area

```html
<table id="menu-table" width="100%" cellpadding="0" cellspacing="0">
    <tr>
        <td class="menu2" id="menu2">                
            <div style="padding:12px 0px 0px 12px;">
                <asp:TextBox ID="SearchTextBox" runat="server" />
            </div>
            <asp:Literal ID="ContentMenuLiteral" runat="server" />
        </td>
        <td>
            <div class="content">
                <asp:ContentPlaceHolder ID="BodyContentPlaceHolder" runat="server">
                </asp:ContentPlaceHolder>
            </div>
        </td>
    </tr>
</table>
```

## Usage

This master page is used as a template for content pages throughout the application. To use it, an ASPX page would specify this master page in its Page directive and then define content for each of the placeholders:

```aspx
<%@ Page Title="" Language="C#" MasterPageFile="~/ContentMaster.Master" AutoEventWireup="true" CodeBehind="ExamplePage.aspx.cs" Inherits="MixERP.Net.FrontEnd.ExamplePage" %>

<asp:Content ID="Content1" ContentPlaceHolderID="ScriptContentPlaceHolder" runat="server">
    <!-- Page-specific scripts -->
</asp:Content>

<asp:Content ID="Content2" ContentPlaceHolderID="StyleSheetContentPlaceHolder" runat="server">
    <!-- Page-specific styles -->
</asp:Content>

<asp:Content ID="Content3" ContentPlaceHolderID="BodyContentPlaceHolder" runat="server">
    <!-- Main page content -->
</asp:Content>

<asp:Content ID="Content4" ContentPlaceHolderID="BottomScriptContentPlaceHolder" runat="server">
    <!-- Scripts to be loaded at the end of the page -->
</asp:Content>
```

## Dependencies

- [MixERPMaster.Master](MixERPMaster.Master.md): The parent master page
- [ContentMaster.Master.cs](ContentMaster.Master.cs.md): Code-behind file that contains the logic for this master page
- [ContentMaster.Master.designer.cs](ContentMaster.Master.designer.cs.md): Designer file that defines the controls for this master page

## License Information

The file is licensed under Mozilla Public License, v. 2.0. If a copy of the MPL was not distributed with this file, you can obtain one at http://mozilla.org/MPL/2.0/.

## Notes

- The menu items displayed in the left panel are dynamically generated in the code-behind file through the `ContentMenuLiteral` control.
- The search functionality provided by the `SearchTextBox` likely works in conjunction with JavaScript to filter menu items.
- The styling of the page is controlled by CSS classes defined elsewhere in the application, particularly the "menu2" and "content" classes.