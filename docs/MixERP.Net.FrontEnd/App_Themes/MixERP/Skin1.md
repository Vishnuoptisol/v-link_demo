# Skin1.skin Documentation

## Overview

`Skin1.skin` is an ASP.NET theme skin file located in the MixERP application's theme folder (`MixERP.Net.FrontEnd\App_Themes\MixERP`). This file defines the default appearance and styling for ASP.NET server controls used throughout the MixERP.Net.FrontEnd application. The skin provides consistent styling for GridView controls used in the application's user interface.

## File Purpose

Skin files in ASP.NET allow developers to define a common look and feel for server controls across multiple web forms without having to repeat styling code. The `Skin1.skin` file specifically provides standardized styling for GridView controls used across the MixERP application.

## Skin Definitions

### GridView Control Skin

The file contains a commented-out definition for styling GridView controls. While currently commented out (inactive), the skin would apply the following styles to all GridView controls in pages that use this theme:

```asp
<asp:GridView runat="server"
    GridLines="None"
    CssClass="grid"
    PagerStyle-CssClass="gridpager"
    RowStyle-CssClass="row"
    AlternatingRowStyle-CssClass="alt">
</asp:GridView>
```

#### Properties:

- **GridLines**: Set to "None" to remove default grid lines
- **CssClass**: Applies the "grid" CSS class to the GridView
- **PagerStyle-CssClass**: Applies the "gridpager" CSS class to the pager section
- **RowStyle-CssClass**: Applies the "row" CSS class to each row
- **AlternatingRowStyle-CssClass**: Applies the "alt" CSS class to alternate rows for a striped effect

## Related Files

- The styles referenced in this skin file (grid, gridpager, row, alt) are likely defined in the [Default.css](MixERP.Net.FrontEnd/App_Themes/MixERP/Default.css.md) file located in the same directory.
- This skin file is used by ASP.NET pages throughout the application via the theme system, particularly those that implement GridView controls, such as various listing and data pages across the application modules.

## Usage Notes

Currently, the GridView style definition is commented out, which means it is not actively being applied. To activate this skin:

1. Remove the comment delimiters (`<%--` and `-%>`) from around the GridView definition
2. Ensure the theme is properly referenced in the application's configuration or page directives

The presence of this commented-out code suggests that either:
- The styling is being applied differently (perhaps through direct CSS)
- This definition is being kept as a reference for future use
- A different styling approach is currently being used for GridView controls in the application

## Theme Integration

This skin file is part of the "MixERP" theme, which is likely referenced in the application's pages via the `Theme="MixERP"` attribute in page directives or through web.config configuration. When properly referenced, ASP.NET automatically applies these styles to controls across the application.