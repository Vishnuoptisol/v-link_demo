# MixERPMaster.Master.cs Documentation

## Overview

`MixERPMaster.Master.cs` is the code-behind file for the MixERP master page template. It provides the core layout structure for the MixERP application. The class is responsible for dynamically loading the application's menu based on user permissions and configuration settings. When a page that uses this master template loads, the system will automatically populate the navigation menu.

## Class Documentation

### MixErpMaster

- **Namespace**: `MixERP.Net.FrontEnd`
- **Type**: Partial class
- **Base Class**: `System.Web.UI.MasterPage`
- **Access Modifier**: Public
- **Purpose**: Serves as the main master page for the MixERP application, handling common UI elements like navigation menus.

## Method Documentation

### Page_Load

- **Access Modifier**: Protected
- **Return Type**: void
- **Parameters**:
  - `sender` (object): The object that triggered the event.
  - `e` (EventArgs): Event arguments.
- **Purpose**: Event handler that executes when the master page loads.
- **Functionality**: Calls the `LoadMenu()` method to populate the navigation menu.

#### Example Usage

The method is automatically called by the ASP.NET page lifecycle:

```csharp
// This method is called automatically when the page loads
protected void Page_Load(object sender, EventArgs e)
{
    this.LoadMenu();
}
```

### LoadMenu

- **Access Modifier**: Private
- **Return Type**: void
- **Parameters**: None
- **Purpose**: Populates the application's navigation menu based on user permissions and configuration.
- **Functionality**:
  1. Initializes an empty menu string.
  2. Retrieves a collection of menu items using `MixERP.Net.BusinessLayer.Core.Menu.GetMenuCollection(0, 0)`.
  3. If the collection contains items, iterates through each menu item.
  4. For each menu item, extracts the menu text and URL.
  5. Builds an HTML anchor tag with the URL and menu text, resolved to the correct path using `ResolveUrl`.
  6. Assigns the generated HTML to the `MenuLiteral` control for display.

#### Example Usage

```csharp
private void LoadMenu()
{
    string menu = string.Empty;

    Collection<MixERP.Net.Common.Models.Core.Menu> collection = MixERP.Net.BusinessLayer.Core.Menu.GetMenuCollection(0, 0);
    if(collection.Count > 0)
    {
        foreach(MixERP.Net.Common.Models.Core.Menu model in collection)
        {
            string menuText = model.MenuText;
            string url = model.Url;
            menu += string.Format(System.Threading.Thread.CurrentThread.CurrentCulture, "<a href='{0}' title='{1}'>{1}</a>", ResolveUrl(url), menuText);
        }
    }

    MenuLiteral.Text = menu;
}
```

## Dependencies

The class depends on several other components within the MixERP system:

1. **MixERP.Net.Common.Models.Core.Menu**: A model class that represents menu items in the system.
2. **MixERP.Net.BusinessLayer.Core.Menu**: A business layer class that provides methods for retrieving menu items.
3. **MenuLiteral**: A control defined in the [MixERPMaster.Master](MixERPMaster.Master.md) file that displays the rendered menu HTML.

## Integration with MixERP

This master page serves as the foundation for the UI across the MixERP application. It ensures consistent navigation and layout throughout the system. The dynamic menu loading mechanism provides role-based access control by potentially filtering menu items based on user permissions (though the sample code passes 0s as parameters to `GetMenuCollection`).

The master page integrates with various other pages in the application, including:
- [Dashboard/Index.aspx](Dashboard/Index.aspx.md)
- [Finance/Index.aspx](Finance/Index.aspx.md)
- [Sales/Index.aspx](Sales/Index.aspx.md)
- [Purchase/Index.aspx](Purchase/Index.aspx.md)
- [Items/Index.aspx](Items/Index.aspx.md)
- And many other module entry points

By providing a consistent navigation structure, this master page enables users to navigate efficiently throughout the MixERP application.