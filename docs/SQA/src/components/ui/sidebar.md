# Sidebar Component Documentation

## Overview

The sidebar component is a comprehensive, customizable navigation sidebar for React applications. It provides a responsive sidebar that can be expanded, collapsed, and toggled between different display modes. The sidebar supports desktop and mobile views, keyboard shortcuts for toggling visibility, and a variety of layout options including floating, inset, and standard sidebars. This component is built using React and integrates with a utility-first CSS approach using Tailwind CSS.

## Dependencies

- React from `react`
- [Slot from @radix-ui/react-slot](https://www.radix-ui.com/primitives/docs/utilities/slot)
- [VariantProps, cva from class-variance-authority](https://cva.style/docs)
- [PanelLeft from lucide-react](https://lucide.dev/)
- Custom hook: `useIsMobile` from `@/hooks/use-mobile`
- [Utils: cn from @/lib/utils](../../../lib/utils.md)
- UI Components:
  - [Button from @/components/ui/button](button.md)
  - [Input from @/components/ui/input](input.md)
  - [Separator from @/components/ui/separator](separator.md)
  - [Sheet, SheetContent from @/components/ui/sheet](sheet.md)
  - [Skeleton from @/components/ui/skeleton](skeleton.md)
  - [Tooltip, TooltipContent, TooltipProvider, TooltipTrigger from @/components/ui/tooltip](tooltip.md)

## Constants

- `SIDEBAR_COOKIE_NAME`: "sidebar_state" - Cookie name used to persist sidebar state
- `SIDEBAR_COOKIE_MAX_AGE`: 604800 (60 * 60 * 24 * 7) - One week in seconds
- `SIDEBAR_WIDTH`: "16rem" - Default sidebar width
- `SIDEBAR_WIDTH_MOBILE`: "18rem" - Mobile sidebar width
- `SIDEBAR_WIDTH_ICON`: "3rem" - Width when collapsed to icon mode
- `SIDEBAR_KEYBOARD_SHORTCUT`: "b" - Key used for keyboard shortcut (Ctrl+B or Cmd+B)

## Context

### SidebarContext

A React Context that provides sidebar state and functions to its children.

#### Type Definition
```typescript
type SidebarContext = {
  state: "expanded" | "collapsed"
  open: boolean
  setOpen: (open: boolean) => void
  openMobile: boolean
  setOpenMobile: (open: boolean) => void
  isMobile: boolean
  toggleSidebar: () => void
}
```

## Hooks

### useSidebar

A custom hook that provides access to the SidebarContext.

```typescript
function useSidebar(): SidebarContext
```

**Returns:** The current SidebarContext value.

**Throws:** Error if used outside of a SidebarProvider.

## Components

### SidebarProvider

The main provider component that wraps the sidebar system and provides context.

```jsx
<SidebarProvider defaultOpen={true}>
  {/* Sidebar components go here */}
</SidebarProvider>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| defaultOpen | boolean | `true` | Initial state of the sidebar |
| open | boolean | `undefined` | Controlled state of the sidebar |
| onOpenChange | (open: boolean) => void | `undefined` | Callback when open state changes |
| className | string | `undefined` | Additional CSS classes |
| style | React.CSSProperties | `undefined` | Inline styles |
| children | React.ReactNode | `undefined` | Child components |

#### Implementation Details

- Manages internal sidebar state
- Persists state using cookies
- Provides keyboard shortcut (Ctrl/Cmd + B)
- Adapts to mobile and desktop views

### Sidebar

The main sidebar component that renders the container for sidebar content.

```jsx
<Sidebar side="left" variant="sidebar" collapsible="offcanvas">
  {/* Sidebar content */}
</Sidebar>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| side | "left" \| "right" | "left" | Which side to render the sidebar |
| variant | "sidebar" \| "floating" \| "inset" | "sidebar" | Visual style variant |
| collapsible | "offcanvas" \| "icon" \| "none" | "offcanvas" | Collapse behavior |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Child components |

#### Implementation Details

- For mobile: Renders a Sheet component
- For desktop: Renders a fixed positioned div
- Adapts layout based on `collapsible` and `variant` props

### SidebarTrigger

A button that toggles the sidebar state when clicked.

```jsx
<SidebarTrigger />
```

#### Props

Extends [Button](button.md) component props.

#### Implementation Details

- Renders a button with a PanelLeft icon
- Calls toggleSidebar from context when clicked

### SidebarRail

A draggable rail on the edge of the sidebar that allows resizing.

```jsx
<SidebarRail />
```

#### Props

Extends standard button props.

#### Implementation Details

- Positioned at the edge of the sidebar
- Includes cursor styling for resize indication
- Toggles the sidebar when clicked

### SidebarInset

Main content container designed to work alongside the sidebar.

```jsx
<SidebarInset>
  {/* Main content */}
</SidebarInset>
```

#### Props

Extends standard div props.

#### Implementation Details

- Adapts its margin based on sidebar state and variant
- Uses peer selectors to respond to sidebar state

### SidebarInput

An input field styled for use within the sidebar.

```jsx
<SidebarInput placeholder="Search..." />
```

#### Props

Extends [Input](input.md) component props.

### SidebarHeader

A container for the top section of the sidebar.

```jsx
<SidebarHeader>
  {/* Header content */}
</SidebarHeader>
```

#### Props

Extends standard div props.

### SidebarFooter

A container for the bottom section of the sidebar.

```jsx
<SidebarFooter>
  {/* Footer content */}
</SidebarFooter>
```

#### Props

Extends standard div props.

### SidebarSeparator

A horizontal divider line for visual separation within the sidebar.

```jsx
<SidebarSeparator />
```

#### Props

Extends [Separator](separator.md) component props.

### SidebarContent

The main content area of the sidebar.

```jsx
<SidebarContent>
  {/* Sidebar main content */}
</SidebarContent>
```

#### Props

Extends standard div props.

#### Implementation Details

- Includes overflow handling
- Takes up available space with flex-1

### SidebarGroup

A grouping container for sidebar menu items.

```jsx
<SidebarGroup>
  {/* Group content */}
</SidebarGroup>
```

#### Props

Extends standard div props.

### SidebarGroupLabel

A label for a sidebar group.

```jsx
<SidebarGroupLabel>Group Title</SidebarGroupLabel>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| asChild | boolean | false | Use the child as the root element |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Label content |

### SidebarGroupAction

An action button displayed in a sidebar group header.

```jsx
<SidebarGroupAction onClick={handleAction}>
  <PlusIcon />
</SidebarGroupAction>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| asChild | boolean | false | Use the child as the root element |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Action button content |

### SidebarGroupContent

Container for the content within a sidebar group.

```jsx
<SidebarGroupContent>
  {/* Group content */}
</SidebarGroupContent>
```

#### Props

Extends standard div props.

### SidebarMenu

A container for a list of menu items in the sidebar.

```jsx
<SidebarMenu>
  {/* Menu items */}
</SidebarMenu>
```

#### Props

Extends standard ul props.

### SidebarMenuItem

An individual menu item container in the sidebar.

```jsx
<SidebarMenuItem>
  {/* Menu item content */}
</SidebarMenuItem>
```

#### Props

Extends standard li props.

### SidebarMenuButton

A clickable button used for navigation within the sidebar menu.

```jsx
<SidebarMenuButton 
  isActive={isCurrentPage}
  tooltip="Dashboard"
  variant="default"
  size="default"
>
  <Icon />
  <span>Menu Item</span>
</SidebarMenuButton>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| asChild | boolean | false | Use the child as the root element |
| isActive | boolean | false | Whether the menu item is currently active |
| tooltip | string \| React.ComponentProps<typeof TooltipContent> | `undefined` | Tooltip content displayed when sidebar is collapsed |
| variant | "default" \| "outline" | "default" | Visual style variant |
| size | "default" \| "sm" \| "lg" | "default" | Size of the button |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Button content |

### SidebarMenuAction

A secondary action button displayed within a menu item.

```jsx
<SidebarMenuAction showOnHover={true} onClick={handleAction}>
  <EditIcon />
</SidebarMenuAction>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| asChild | boolean | false | Use the child as the root element |
| showOnHover | boolean | false | Only show the action on hover |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Action button content |

### SidebarMenuBadge

A badge displayed within a menu item to show notifications or counts.

```jsx
<SidebarMenuBadge>3</SidebarMenuBadge>
```

#### Props

Extends standard div props.

### SidebarMenuSkeleton

A skeleton loader for menu items when loading content.

```jsx
<SidebarMenuSkeleton showIcon={true} />
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| showIcon | boolean | false | Whether to show an icon placeholder |
| className | string | `undefined` | Additional CSS classes |

### SidebarMenuSub

A submenu container for nested menu items.

```jsx
<SidebarMenuSub>
  {/* Submenu items */}
</SidebarMenuSub>
```

#### Props

Extends standard ul props.

### SidebarMenuSubItem

An individual submenu item container.

```jsx
<SidebarMenuSubItem>
  {/* Submenu item content */}
</SidebarMenuSubItem>
```

#### Props

Extends standard li props.

### SidebarMenuSubButton

A clickable button for submenu navigation.

```jsx
<SidebarMenuSubButton 
  isActive={isCurrentPage}
  size="md"
  href="/dashboard/settings"
>
  <span>Submenu Item</span>
</SidebarMenuSubButton>
```

#### Props

| Name | Type | Default | Description |
|------|------|---------|-------------|
| asChild | boolean | false | Use the child as the root element |
| size | "sm" \| "md" | "md" | Size of the button |
| isActive | boolean | `undefined` | Whether the submenu item is active |
| className | string | `undefined` | Additional CSS classes |
| children | React.ReactNode | `undefined` | Button content |

## Usage Examples

### Basic Sidebar

```jsx
import { 
  Sidebar, 
  SidebarProvider, 
  SidebarContent, 
  SidebarHeader,
  SidebarFooter,
  SidebarMenu,
  SidebarMenuItem,
  SidebarMenuButton
} from "@/components/ui/sidebar";

export function AppSidebar() {
  return (
    <SidebarProvider>
      <Sidebar>
        <SidebarHeader>
          <Logo />
        </SidebarHeader>
        <SidebarContent>
          <SidebarMenu>
            <SidebarMenuItem>
              <SidebarMenuButton isActive={true}>
                <HomeIcon />
                <span>Dashboard</span>
              </SidebarMenuButton>
            </SidebarMenuItem>
            <SidebarMenuItem>
              <SidebarMenuButton>
                <UsersIcon />
                <span>Users</span>
              </SidebarMenuButton>
            </SidebarMenuItem>
          </SidebarMenu>
        </SidebarContent>
        <SidebarFooter>
          <UserProfile />
        </SidebarFooter>
      </Sidebar>
      <SidebarInset>
        {/* Main content */}
      </SidebarInset>
    </SidebarProvider>
  );
}
```

### Sidebar with Nested Submenus

```jsx
<SidebarMenu>
  <SidebarMenuItem>
    <SidebarMenuButton>
      <SettingsIcon />
      <span>Settings</span>
    </SidebarMenuButton>
    <SidebarMenuSub>
      <SidebarMenuSubItem>
        <SidebarMenuSubButton isActive={true}>
          <span>Profile</span>
        </SidebarMenuSubButton>
      </SidebarMenuSubItem>
      <SidebarMenuSubItem>
        <SidebarMenuSubButton>
          <span>Security</span>
        </SidebarMenuSubButton>
      </SidebarMenuSubItem>
    </SidebarMenuSub>
  </SidebarMenuItem>
</SidebarMenu>
```

### Floating Sidebar with Custom Actions

```jsx
<SidebarProvider>
  <Sidebar variant="floating" collapsible="icon">
    <SidebarHeader>
      <Logo />
      <SidebarTrigger />
    </SidebarHeader>
    <SidebarContent>
      <SidebarGroup>
        <SidebarGroupLabel>Projects</SidebarGroupLabel>
        <SidebarGroupAction>
          <PlusIcon />
        </SidebarGroupAction>
        <SidebarMenu>
          {isLoading ? (
            <>
              <SidebarMenuSkeleton showIcon={true} />
              <SidebarMenuSkeleton showIcon={true} />
            </>
          ) : (
            projects.map(project => (
              <SidebarMenuItem key={project.id}>
                <SidebarMenuButton tooltip={project.name}>
                  <FolderIcon />
                  <span>{project.name}</span>
                </SidebarMenuButton>
                <SidebarMenuBadge>{project.taskCount}</SidebarMenuBadge>
                <SidebarMenuAction showOnHover={true}>
                  <DotsHorizontalIcon />
                </SidebarMenuAction>
              </SidebarMenuItem>
            ))
          )}
        </SidebarMenu>
      </SidebarGroup>
    </SidebarContent>
  </Sidebar>
  <SidebarInset>
    {/* Main content */}
  </SidebarInset>
</SidebarProvider>
```

This sidebar component provides a robust, accessible, and highly customizable navigation system that adapts to both mobile and desktop views while maintaining a consistent user experience.