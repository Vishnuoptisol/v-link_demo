# Dropdown Menu Component Documentation

## Overview

The dropdown menu component provides a flexible and accessible menu system for displaying various options in a dropdown interface. It's built on top of Radix UI's Dropdown Menu primitive components, styled with Tailwind CSS using the `cn` utility function for class name merging. This component supports various dropdown menu features including nested submenus, checkbox items, radio items, labels, and keyboard shortcuts.

## Dependencies

- React core functionality via the `"use client"` directive for client-side component rendering
- Radix UI dropdown menu primitives from `@radix-ui/react-dropdown-menu`
- Icon components (`Check`, `ChevronRight`, `Circle`) from `lucide-react`
- Utility function `cn` from [utils.ts](../../lib/utils.md) for class name composition

## Component Documentation

### Root Components

#### `DropdownMenu`
- **Purpose**: Serves as the root container for the dropdown menu system
- **Type**: Direct re-export of `DropdownMenuPrimitive.Root`
- **Usage**: Wraps all dropdown menu components

#### `DropdownMenuTrigger`
- **Purpose**: Element that triggers the dropdown menu to open when interacted with
- **Type**: Direct re-export of `DropdownMenuPrimitive.Trigger`
- **Usage**: Used as the clickable element to show/hide the dropdown

#### `DropdownMenuGroup`
- **Purpose**: Groups dropdown menu items together
- **Type**: Direct re-export of `DropdownMenuPrimitive.Group`

#### `DropdownMenuPortal`
- **Purpose**: Renders dropdown content in a portal, outside the DOM hierarchy
- **Type**: Direct re-export of `DropdownMenuPrimitive.Portal`

#### `DropdownMenuSub`
- **Purpose**: Container for submenu content
- **Type**: Direct re-export of `DropdownMenuPrimitive.Sub`

#### `DropdownMenuRadioGroup`
- **Purpose**: Container for radio items
- **Type**: Direct re-export of `DropdownMenuPrimitive.RadioGroup`

### Enhanced Components

#### `DropdownMenuSubTrigger`
- **Purpose**: Trigger element for opening a submenu
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `inset`: Boolean to apply padding offset for visual hierarchy
  - `children`: React nodes to render inside the trigger
  - Additional props spread to the underlying `DropdownMenuPrimitive.SubTrigger`
- **Implementation**:
  - Adds styling and a chevron icon to indicate submenu presence
  - Handles keyboard navigation and focus states

#### `DropdownMenuSubContent`
- **Purpose**: Container for submenu items
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - Additional props spread to the underlying `DropdownMenuPrimitive.SubContent`
- **Implementation**:
  - Applies styling, animations, and positioning for submenu content

#### `DropdownMenuContent`
- **Purpose**: Container for the main dropdown menu items
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `sideOffset`: Distance in pixels from the trigger (defaults to 4px)
  - Additional props spread to the underlying `DropdownMenuPrimitive.Content`
- **Implementation**:
  - Wraps content in a portal for proper stacking context
  - Applies styling, animations, and positioning for dropdown content

#### `DropdownMenuItem`
- **Purpose**: Standard menu item for dropdown options
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `inset`: Boolean to apply padding offset for visual hierarchy
  - Additional props spread to the underlying `DropdownMenuPrimitive.Item`
- **Implementation**:
  - Styles menu items with proper spacing and focus states
  - Supports icons with consistent sizing

#### `DropdownMenuCheckboxItem`
- **Purpose**: Checkbox item for togglable options
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `children`: React nodes to render inside the item
  - `checked`: Boolean for the checkbox state
  - Additional props spread to the underlying `DropdownMenuPrimitive.CheckboxItem`
- **Implementation**:
  - Displays a check icon when checked
  - Handles selection states and keyboard interactions

#### `DropdownMenuRadioItem`
- **Purpose**: Radio item for mutually exclusive options
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `children`: React nodes to render inside the item
  - Additional props spread to the underlying `DropdownMenuPrimitive.RadioItem`
- **Implementation**:
  - Displays a filled circle icon when selected
  - Handles selection states and keyboard interactions

#### `DropdownMenuLabel`
- **Purpose**: Text label for categorizing menu items
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - `inset`: Boolean to apply padding offset for visual hierarchy
  - Additional props spread to the underlying `DropdownMenuPrimitive.Label`
- **Implementation**:
  - Applies styling for non-interactive text labels

#### `DropdownMenuSeparator`
- **Purpose**: Visual divider between menu items
- **Type**: `React.ForwardRefExoticComponent`
- **Props**:
  - `className`: Custom CSS class name
  - Additional props spread to the underlying `DropdownMenuPrimitive.Separator`
- **Implementation**:
  - Renders a horizontal line to visually separate groups of items

#### `DropdownMenuShortcut`
- **Purpose**: Displays keyboard shortcuts for menu items
- **Type**: `React.FC<React.HTMLAttributes<HTMLSpanElement>>`
- **Props**:
  - `className`: Custom CSS class name
  - Additional props spread to the underlying `span` element
- **Implementation**:
  - Renders text with specialized styling for keyboard shortcuts
  - Positioned at the end of menu items

## Usage Examples

### Basic Dropdown Menu

```tsx
<DropdownMenu>
  <DropdownMenuTrigger>Open Menu</DropdownMenuTrigger>
  <DropdownMenuContent>
    <DropdownMenuItem>Profile</DropdownMenuItem>
    <DropdownMenuItem>Settings</DropdownMenuItem>
    <DropdownMenuSeparator />
    <DropdownMenuItem>Logout</DropdownMenuItem>
  </DropdownMenuContent>
</DropdownMenu>
```

### Dropdown Menu with Submenu

```tsx
<DropdownMenu>
  <DropdownMenuTrigger>Open Menu</DropdownMenuTrigger>
  <DropdownMenuContent>
    <DropdownMenuItem>Dashboard</DropdownMenuItem>
    <DropdownMenuSub>
      <DropdownMenuSubTrigger>More Options</DropdownMenuSubTrigger>
      <DropdownMenuSubContent>
        <DropdownMenuItem>Import</DropdownMenuItem>
        <DropdownMenuItem>Export</DropdownMenuItem>
      </DropdownMenuSubContent>
    </DropdownMenuSub>
  </DropdownMenuContent>
</DropdownMenu>
```

### Dropdown with Checkbox and Radio Items

```tsx
<DropdownMenu>
  <DropdownMenuTrigger>Open Menu</DropdownMenuTrigger>
  <DropdownMenuContent>
    <DropdownMenuLabel>View Options</DropdownMenuLabel>
    <DropdownMenuCheckboxItem checked={true}>Show Line Numbers</DropdownMenuCheckboxItem>
    <DropdownMenuCheckboxItem>Word Wrap</DropdownMenuCheckboxItem>
    <DropdownMenuSeparator />
    <DropdownMenuLabel>Theme</DropdownMenuLabel>
    <DropdownMenuRadioGroup value="light">
      <DropdownMenuRadioItem value="light">Light</DropdownMenuRadioItem>
      <DropdownMenuRadioItem value="dark">Dark</DropdownMenuRadioItem>
      <DropdownMenuRadioItem value="system">System</DropdownMenuRadioItem>
    </DropdownMenuRadioGroup>
  </DropdownMenuContent>
</DropdownMenu>
```

## Accessibility

The dropdown menu component is built on Radix UI primitives, which provide robust keyboard navigation, focus management, and ARIA attributes for accessibility. Users can navigate the menu using keyboard controls, and screen readers will announce menu items appropriately.