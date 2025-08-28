# Dashboard/Index.aspx Documentation

## Overview

`Index.aspx` is the main dashboard page of the MixERP application. It provides a customizable, widget-based interface using the Gridster.js library to present various business metrics and actionable information to users. The dashboard displays sales statistics by office and month, workflow items, office information, alerts, quick links, and top-selling products information using a grid layout that allows for widget repositioning.

## Page Structure

### Master Page
This page inherits from [MenuMaster.Master](../MenuMaster.Master.md), which provides the common layout and navigation elements.

### Controls and Libraries
- **Gridster.js**: A jQuery plugin that allows for responsive, draggable, and resizable grid layouts.
- **System.Web.UI.DataVisualization.Charting**: A .NET library for creating charts and data visualizations.

### Widgets Used
The dashboard includes several custom widgets:

1. **SalesByOfficeWidget**: Shows sales data aggregated by office
2. **CurrentOfficeSalesByMonthWidget**: Displays sales trends for the current office by month
3. **WorkflowWidget**: Shows workflow items that require attention
4. **OfficeInformationWidget**: Provides summary information about the current office
5. **AlertsWidget**: Displays system and business alerts
6. **LinksWidget**: Provides quick access to commonly used functions
7. **TopSellingProductOfAllTimetWidget**: Shows top-selling products of all time
8. **TopSellingProductOfAllTimeCurrentWidget**: Shows top-selling products for the current period

## Content Placeholders

### ScriptContentPlaceHolder
Contains JavaScript initialization for the Gridster library:
```javascript
var gridster;

$(function () {
    gridster = $(".gridster > ul").gridster({
        widget_margins: [10, 10],
        widget_base_dimensions: [116, 122],
        min_cols: 2
    }).data('gridster');
});
```

Also includes a CSS style to remove list markers:
```css
ul, ol {
    list-style: none;
}
```

### StyleSheetContentPlaceHolder
No additional stylesheets are included in this placeholder.

### BodyContentPlaceHolder
Contains:
1. A welcome heading (hardcoded for "Binod")
2. The Gridster container with a list of widgets arranged in a grid
3. Control buttons for managing the dashboard layout

### BottomScriptContentPlaceHolder
No additional scripts are included in this placeholder.

## Widget Layout

The dashboard uses a grid-based layout with the following arrangement:
- First row: Two wide widgets (4 columns each) for sales statistics
- Second row: Four smaller widgets (2 columns each) for workflow, office info, alerts, and quick links
- Third row: Two wide widgets (4 columns each) for top-selling products statistics

Each widget has a specified position (`data-row`, `data-col`) and size (`data-sizex`, `data-sizey`) within the Gridster grid.

## Control Buttons

The dashboard includes three action buttons:
1. **SavePositionButton**: Saves the current arrangement of widgets
2. **ResetPositionButton**: Resets widgets to their default positions
3. **GoToWidgetManagerButton**: Link to a widget management page (noted as "Todo: Admin Only")

## Widget Components

### SalesByOfficeWidget
The widget is defined in [UserControls/Widgets/SalesByOfficeWidget.ascx](../UserControls/Widgets/SalesByOfficeWidget.ascx.md) and displays sales data across different offices.

### CurrentOfficeSalesByMonthWidget
The widget is defined in [UserControls/Widgets/CurrentOfficeSalesByMonthWidget.ascx](../UserControls/Widgets/CurrentOfficeSalesByMonthWidget.ascx.md) and shows monthly sales trends for the current office.

### WorkflowWidget
The widget is defined in [UserControls/Widgets/WorkflowWidget.ascx](../UserControls/Widgets/WorkflowWidget.ascx.md) and displays workflow items that require the user's attention.

### OfficeInformationWidget
The widget is defined in [UserControls/Widgets/OfficeInformationWidget.ascx](../UserControls/Widgets/OfficeInformationWidget.ascx.md) and shows summary information about the current office.

### AlertsWidget
The widget is defined in [UserControls/Widgets/AlertsWidget.ascx](../UserControls/Widgets/AlertsWidget.ascx.md) and displays system alerts and notifications.

### LinksWidget
The widget is defined in [UserControls/Widgets/LinksWidget.ascx](../UserControls/Widgets/LinksWidget.ascx.md) and provides quick links to frequently used functions.

### TopSellingProductOfAllTimetWidget
The widget is defined in [UserControls/Widgets/TopSellingProductOfAllTimetWidget.ascx](../UserControls/Widgets/TopSellingProductOfAllTimetWidget.ascx.md) and shows the overall top-selling products.

### TopSellingProductOfAllTimeCurrentWidget
The widget is defined in [UserControls/Widgets/TopSellingProductOfAllTimeCurrentWidget.ascx](../UserControls/Widgets/TopSellingProductOfAllTimeCurrentWidget.ascx.md) and displays the top-selling products for the current period.

## Implementation Details

The page uses a responsive grid layout that allows for:
- Widget repositioning via drag-and-drop
- Consistent spacing (10px margins between widgets)
- Base widget dimensions of 116×122 pixels
- Minimum of 2 columns for the grid layout
- Total dashboard width of 1092px, centered on the page

## Additional Notes

1. The dashboard has a "Todo Page" label in the title, suggesting it may be under development.
2. The widget management functionality appears to be admin-restricted (based on button text).
3. The welcome message contains a hardcoded name "Binod" rather than a dynamically generated user name.

## Related Files

- [Index.aspx.cs](../Dashboard/Index.aspx.cs.md): Code-behind file for this dashboard
- [Index.aspx.designer.cs](../Dashboard/Index.aspx.designer.cs.md): Designer file for this dashboard