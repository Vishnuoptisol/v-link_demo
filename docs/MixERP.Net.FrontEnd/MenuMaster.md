# MenuMaster.Master Documentation

## Overview

`MenuMaster.Master` is a master page file in the MixERP.Net.FrontEnd application that provides a nested master page structure. It inherits from [MixERPMaster.Master](MixERPMaster.Master.md) and defines content placeholders for scripts, stylesheets, and body content. This master page serves as an intermediate template that can be used by content pages requiring menu functionality while inheriting the base layout from MixERPMaster.

## Master Page Documentation

### File Information
- **Language**: ASP.NET (C#)
- **Inherits From**: [MixERPMaster.Master](MixERPMaster.Master.md)
- **Code Behind**: [MenuMaster.Master.cs](MenuMaster.Master.cs.md)

### Content Placeholders

The master page defines the following content placeholders:

1. **ScriptContentPlaceHolder**
   - Purpose: Contains JavaScript and other script elements that need to be added to the page
   - Location: Appears in the head section of the document (inherited from parent master)
   - Usage: Child pages can inject scripts into this placeholder

2. **StyleSheetContentPlaceHolder**
   - Purpose: Contains CSS and style-related elements
   - Location: Appears in the head section of the document (inherited from parent master)
   - Usage: Child pages can inject stylesheets into this placeholder

3. **BodyContentPlaceHolder**
   - Purpose: Contains the main content of the page
   - Location: Inside a div with class "content"
   - Usage: Child pages will place their main content here

4. **BottomScriptContentPlaceHolder**
   - Purpose: Contains scripts that need to be loaded at the bottom of the page
   - Location: At the end of the body section (inherited from parent master)
   - Usage: Child pages can add scripts that should load after the page content

### Structure

The master page is structured as follows:
```
MixERPMaster.Master (Parent)
└── MenuMaster.Master
    ├── ScriptContentPlaceHolder
    ├── StyleSheetContentPlaceHolder
    ├── BodyContentPlaceHolder (wrapped in a div with class "content")
    └── BottomScriptContentPlaceHolder
```

## Usage

The MenuMaster.Master is intended to be used as a parent for content pages that require the menu functionality. To use this master page, content pages should:

1. Set the `MasterPageFile` attribute to "~/MenuMaster.Master"
2. Implement the content placeholders as needed

### Example Usage

```aspx
<%@ Page Title="Example Page" Language="C#" MasterPageFile="~/MenuMaster.Master" AutoEventWireup="true" CodeBehind="ExamplePage.aspx.cs" Inherits="MixERP.Net.FrontEnd.ExamplePage" %>

<asp:Content ID="Content1" ContentPlaceHolderID="ScriptContentPlaceHolder" runat="server">
    <script src="example.js"></script>
</asp:Content>

<asp:Content ID="Content2" ContentPlaceHolderID="StyleSheetContentPlaceHolder" runat="server">
    <link rel="stylesheet" href="example.css" />
</asp:Content>

<asp:Content ID="Content3" ContentPlaceHolderID="BodyContentPlaceHolder" runat="server">
    <h1>Example Content</h1>
    <p>This is the main content of the page.</p>
</asp:Content>

<asp:Content ID="Content4" ContentPlaceHolderID="BottomScriptContentPlaceHolder" runat="server">
    <script>
        // Scripts that need to be loaded after the page content
    </script>
</asp:Content>
```

## License

The file is licensed under the Mozilla Public License, v. 2.0. The copyright is held by Binod Nepal, Mix Open Foundation (http://mixof.org).

## Related Files

- [MixERPMaster.Master](MixERPMaster.Master.md): The parent master page from which MenuMaster.Master inherits
- [MenuMaster.Master.cs](MenuMaster.Master.cs.md): The code-behind file that defines the behavior of the MenuMaster class
- [MenuMaster.Master.designer.cs](MenuMaster.Master.designer.cs.md): Auto-generated file that contains the declaration of the web form controls