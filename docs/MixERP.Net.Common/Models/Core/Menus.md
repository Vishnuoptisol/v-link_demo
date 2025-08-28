# Menu Class Documentation

## Overview

The `Menu` class, defined in the file `MixERP.Net.Common\Models\Core\Menus.cs`, serves as a data model for representing menu items within the MixERP application. This class is part of the `MixERP.Net.Common.Models.Core` namespace and provides a structured way to store and access menu-related information including menu text, URLs, hierarchical organization, and identification details.

This class is essential for building navigation structures within the application and is likely used by the menu-building components in the system, such as those in [MenuHelper.cs](../../MixERP.Net.BusinessLayer/Helpers/MenuHelper.md) that would generate and manage application menus.

## Class Documentation

### Menu

```csharp
public class Menu
```

**Purpose**: Represents a menu item in the MixERP application's navigation structure.

**Access Modifier**: `public`

**Properties**:

| Property | Type | Description |
|----------|------|-------------|
| `MenuId` | `int` | Unique identifier for the menu item |
| `MenuText` | `string` | Display text shown for the menu item |
| `Url` | `string` | Navigation URL or path associated with the menu item |
| `MenuCode` | `string` | Code identifier for the menu item, likely used for programmatic reference |
| `Level` | `int` | Hierarchical level of the menu item in the menu tree structure |
| `ParentMenuId` | `int` | Reference to the parent menu item's ID, establishing a parent-child relationship |

**Constructors**: 
- Default constructor (implicitly defined)

## Usage Examples

### Creating a Menu Item

```csharp
// Create a new top-level menu item
Menu mainMenu = new Menu
{
    MenuId = 1,
    MenuText = "Dashboard",
    Url = "~/Dashboard/Index.aspx",
    MenuCode = "DASH",
    Level = 0,
    ParentMenuId = 0
};

// Create a submenu item
Menu subMenu = new Menu
{
    MenuId = 2,
    MenuText = "Sales Overview",
    Url = "~/Dashboard/Sales.aspx",
    MenuCode = "DASH-SALES",
    Level = 1,
    ParentMenuId = 1
};
```

### Building a Menu Hierarchy

```csharp
// Example of organizing menus in a hierarchical structure
List<Menu> menuCollection = new List<Menu>();

// Add parent menu
Menu parentMenu = new Menu
{
    MenuId = 100,
    MenuText = "Finance",
    Url = "#",
    MenuCode = "FIN",
    Level = 0,
    ParentMenuId = 0
};
menuCollection.Add(parentMenu);

// Add child menus
Menu childMenu1 = new Menu
{
    MenuId = 101,
    MenuText = "Journal Voucher",
    Url = "~/Finance/JournalVoucher.aspx",
    MenuCode = "FIN-JV",
    Level = 1,
    ParentMenuId = 100
};
menuCollection.Add(childMenu1);

Menu childMenu2 = new Menu
{
    MenuId = 102,
    MenuText = "Bank Reconciliation",
    Url = "~/Finance/BankReconciliation.aspx",
    MenuCode = "FIN-BR",
    Level = 1,
    ParentMenuId = 100
};
menuCollection.Add(childMenu2);
```

## Related Components

This model class is likely utilized by the following components in the MixERP application:

- Menu management and rendering systems
- Navigation components
- Permission and access control systems that need to reference menu items
- The [Menu.cs](../../MixERP.Net.BusinessLayer/Core/Menu.md) class in the business layer, which would handle the business logic related to menus
- [Menu.cs](../../MixERP.Net.DatabaseLayer/Core/Menu.md) in the database layer for persisting menu data

## Notes

- The hierarchical structure is established through the `Level` and `ParentMenuId` properties.
- The `MenuCode` property likely serves as a unique identifier for programmatic reference, while `MenuId` serves as a database primary key.
- The class follows a simple POCO (Plain Old CLR Object) design pattern with properties for data binding.