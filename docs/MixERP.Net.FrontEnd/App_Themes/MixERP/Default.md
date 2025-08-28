# Default.css Documentation

## Overview

The `Default.css` file serves as the primary stylesheet for the MixERP.Net.FrontEnd application. This stylesheet defines the fundamental visual presentation across the application, including typography, form elements, tables, and specialized UI components like sign-in panels, report parameters, and loading indicators.

## CSS Rules Documentation

### Typography

```css
html, body, table, tr, td, h1, h2, h3, h4, h5, input, select, p, textarea
{
    font-family: 'Segoe UI', 'Tahoma', 'Arial';
}
```

This rule establishes a consistent font family across all basic HTML elements, prioritizing Segoe UI with Tahoma and Arial as fallbacks. It's applied globally to ensure typographic consistency throughout the application.

### Sign-In Components

#### Sign-In Logo

```css
.sign-in-logo
{
    width: 300px;
    margin: auto;
    margin-top: 160px;
}
```

This class styles the logo that appears on the [SignIn.aspx](SignIn.aspx.md) page. It centers the logo horizontally with a fixed width of 300px and positions it 160px from the top of the page.

#### Sign-In Container

```css
.sign-in
{
    width: 300px;
    margin: auto;
    height: 240px;
    background-color: #F0F0F0;
    padding: 12px;
}

.sign-in:hover
{
    background-color: #F0F0E0;
}
```

These rules style the sign-in form container used in [SignIn.aspx](SignIn.aspx.md), creating a centered box with light gray background that changes to a subtle beige color when hovered.

### Link Styling

```css
a img
{
    border: none;
}

a
{
    text-decoration: none;
}
```

These rules remove the default underline from all links and eliminate borders around linked images across the application.

### Hover Transition Effects

```css
h1:hover, h2:hover, h3:hover, h4:hover, h5:hover, h6:hover, a:hover, span:hover, table:hover, tr:hover, td:hover, div:hover
{
    -webkit-transition: all 500ms ease;
    -moz-transition: all 500ms ease;
    -o-transition: all 500ms ease;
    -ms-transition: all 500ms ease;
    transition: all 500ms ease;
}
```

This rule adds a smooth 500ms transition effect when users hover over various HTML elements, creating a more fluid and responsive UI experience.

### AJAX Loading Components

```css
.ajax-container
{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1000;
    background-color: #A7D0D9;
    opacity: .5;
}

.ajax-loader
{
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -32px;
    margin-top: -32px;
    display: block;
    opacity: 0.9;
}
```

These classes define the loading overlay and spinner used during AJAX requests. The container creates a semi-transparent blue overlay that covers the entire page, while the loader is centered precisely in the middle of the screen.

### Report Components

#### Report Parameter

```css
.report-parameter
{
    border: 1px solid #EDCAF7;
    background-color: #F8EBFC;
    position: absolute;
    right: 20px;
    top: 50px;
    padding: 12px;
}

.report-parameter table
{
    border-collapse: collapse;
    color: #8F16B8;
}

.report-parameter table tr td, .report-parameter table tr td input
{
    outline: none;
    font-size: 11px;
    color: #8F16B8;
}

.report-parameter table tr td input
{
    border: 1px solid #F3DFFF;
}

.report-parameter table tr td:first-child
{
    padding: 4px;
    width: 132px;
}
```

These rules style the report parameter panel used in reports like those found in the [Reports](../Reports/ReportViewer.aspx.md) section. The panel features a light purple theme with specific styling for tables and inputs inside it.

### Body and General Elements

```css
body
{
    font-size: 11px!important;
}

hr
{
    border: 1px solid gray;
    border-top: 0px;
}
```

These rules set the base font size for the entire application to 11px and style horizontal rules with a consistent gray appearance.

### Tables

```css
table.report tr th, table.report tr td
{
    padding: 4px;
}

.table
{
    border-collapse: collapse;
    border: 1px solid gray;
    min-width: 400px;
}

.table td
{
    border: 1px solid gray;
    padding: 4px!important;
}

table.horizontal > tbody > tr > td:first-child
{
    width: 180px;
    font-weight: bold;
}
```

These rules define various table styles used throughout the application:
- `.report` class is used for report tables with minimal padding
- `.table` class creates standard data tables with borders and minimum width
- `.horizontal` class is used for tables with label-value pairs, where the first column acts as a bold label

### Report Command

```css
.report-command
{
    border: 1px solid #EDCAF7;
    position: absolute;
    padding: 4px 12px 4px 12px;
    top: 20px;
    right: 20px;
    background-color: #F8EBFC;
}

.report-command:hover
{
    background-color: #F2DAFA;
}
```

These rules style the command buttons in report pages, positioning them in the upper right corner with a light purple theme that darkens slightly when hovered.

### Print Media Query

```css
@media print
{
    .hide
    {
        display: none;
    }
}
```

This media query ensures elements with the `.hide` class are not displayed when printing reports or other content.

### Legend

```css
.legend .legend-title {
    margin: 0.5em;
    border-style: solid;
    border-width: 0 0 0 1em;
    padding: 0 0.3em;
}
```

This rule styles legend titles used in charts and graphs, particularly in widgets like [SalesByOfficeWidget](../UserControls/Widgets/SalesByOfficeWidget.ascx.md) and other dashboard components, adding a colored bar to the left of each legend title.

## Related Files

- [MixERPMaster.Master](../MixERPMaster.Master.md): The master page that includes this CSS file
- [MenuMaster.Master](../MenuMaster.Master.md): Secondary master page that inherits styles from this file
- [ContentMaster.Master](../ContentMaster.Master.md): Content master page that applies these styles
- [SignIn.aspx](../SignIn.aspx.md): Uses the sign-in specific styles
- [Themes/purple/main.css](../Themes/purple/main.css.md): Complements this default stylesheet with theme-specific styles

## Usage

This CSS file is referenced in the master pages and applied throughout the MixERP.Net.FrontEnd application. It provides the base styling for all pages and controls, establishing the visual foundation of the application.