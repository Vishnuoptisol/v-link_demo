# Menubar Component Documentation

## Overview

The menubar component provides a comprehensive, accessible horizontal menu system for navigation and command interfaces in the application. Built on top of [Radix UI's](https://radix-ui.com/) Menubar primitive, this component offers a styled, flexible API for creating hierarchical menus with support for submenus, checkboxes, radio items, and keyboard shortcuts.

This component utilizes the [`cn` utility function](../../../lib/utils.md) from the project's utility library to handle conditional class name joining.

## Component Documentation

### Menubar Components

The file exports multiple components that make up the menubar system:

#### `Menubar`

**Purpose**: The root container of the menubar system.

```tsx
const Menubar = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Root>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Root>
>(({ className, ...props }, ref) => (
  <MenubarPrimitive.Root
    ref={ref}
    className={cn(
      "flex h-10 items-center space-x-1 rounded-md border bg-background p-1",
      className
    )}
    {...props}
  />
))
```

**Attributes**:
- Accepts all props from Radix UI's MenubarPrimitive.Root
- `className`: Additional CSS classes to apply to the component

**Usage Example**:
```tsx
<Menubar>
  <MenubarMenu>
    <MenubarTrigger>File</MenubarTrigger>
    <MenubarContent>
      {/* Menu items */}
    </MenubarContent>
  </MenubarMenu>
</Menubar>
```

#### `MenubarMenu`

**Purpose**: Represents an individual menu within the menubar.

```tsx
function MenubarMenu({
  ...props
}: React.ComponentProps<typeof MenubarPrimitive.Menu>) {
  return <MenubarPrimitive.Menu {...props} />
}
```

**Attributes**:
- Passes all props directly to the underlying Radix UI component

#### `MenubarTrigger`

**Purpose**: The clickable button that opens a menu.

```tsx
const MenubarTrigger = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Trigger>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Trigger>
>(({ className, ...props }, ref) => (
  <MenubarPrimitive.Trigger
    ref={ref}
    className={cn(
      "flex cursor-default select-none items-center rounded-sm px-3 py-1.5 text-sm font-medium outline-none focus:bg-accent focus:text-accent-foreground data-[state=open]:bg-accent data-[state=open]:text-accent-foreground",
      className
    )}
    {...props}
  />
))
```

**Attributes**:
- `className`: Additional CSS classes to apply to the component
- All standard props from Radix UI's MenubarPrimitive.Trigger

#### `MenubarContent`

**Purpose**: The container for menu items that appears when a trigger is activated.

```tsx
const MenubarContent = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Content>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Content>
>(
  (
    { className, align = "start", alignOffset = -4, sideOffset = 8, ...props },
    ref
  ) => (
    <MenubarPrimitive.Portal>
      <MenubarPrimitive.Content
        ref={ref}
        align={align}
        alignOffset={alignOffset}
        sideOffset={sideOffset}
        className={cn(
          "z-50 min-w-[12rem] overflow-hidden rounded-md border bg-popover p-1 text-popover-foreground shadow-md data-[state=open]:animate-in data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0 data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-95 data-[side=bottom]:slide-in-from-top-2 data-[side=left]:slide-in-from-right-2 data-[side=right]:slide-in-from-left-2 data-[side=top]:slide-in-from-bottom-2",
          className
        )}
        {...props}
      />
    </MenubarPrimitive.Portal>
  )
)
```

**Attributes**:
- `className`: Additional CSS classes
- `align`: Alignment of the content relative to the trigger ("start", "center", "end")
- `alignOffset`: Pixel offset for alignment
- `sideOffset`: Distance from the trigger

#### `MenubarItem`

**Purpose**: An individual menu item.

```tsx
const MenubarItem = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Item>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Item> & {
    inset?: boolean
  }
>(({ className, inset, ...props }, ref) => (
  <MenubarPrimitive.Item
    ref={ref}
    className={cn(
      "relative flex cursor-default select-none items-center rounded-sm px-2 py-1.5 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[disabled]:pointer-events-none data-[disabled]:opacity-50",
      inset && "pl-8",
      className
    )}
    {...props}
  />
))
```

**Attributes**:
- `className`: Additional CSS classes
- `inset`: Boolean that when true adds left padding for alignment with checkbox/radio items

#### `MenubarCheckboxItem`

**Purpose**: A menu item with a checkbox.

```tsx
const MenubarCheckboxItem = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.CheckboxItem>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.CheckboxItem>
>(({ className, children, checked, ...props }, ref) => (
  <MenubarPrimitive.CheckboxItem
    ref={ref}
    className={cn(
      "relative flex cursor-default select-none items-center rounded-sm py-1.5 pl-8 pr-2 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[disabled]:pointer-events-none data-[disabled]:opacity-50",
      className
    )}
    checked={checked}
    {...props}
  >
    <span className="absolute left-2 flex h-3.5 w-3.5 items-center justify-center">
      <MenubarPrimitive.ItemIndicator>
        <Check className="h-4 w-4" />
      </MenubarPrimitive.ItemIndicator>
    </span>
    {children}
  </MenubarPrimitive.CheckboxItem>
))
```

**Attributes**:
- `className`: Additional CSS classes
- `checked`: Boolean state of the checkbox
- `children`: Content of the menu item

#### `MenubarRadioGroup` and `MenubarRadioItem`

**Purpose**: Group of radio items, where only one can be selected at a time.

```tsx
function MenubarRadioGroup({
  ...props
}: React.ComponentProps<typeof MenubarPrimitive.RadioGroup>) {
  return <MenubarPrimitive.RadioGroup {...props} />
}

const MenubarRadioItem = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.RadioItem>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.RadioItem>
>(({ className, children, ...props }, ref) => (
  <MenubarPrimitive.RadioItem
    ref={ref}
    className={cn(
      "relative flex cursor-default select-none items-center rounded-sm py-1.5 pl-8 pr-2 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[disabled]:pointer-events-none data-[disabled]:opacity-50",
      className
    )}
    {...props}
  >
    <span className="absolute left-2 flex h-3.5 w-3.5 items-center justify-center">
      <MenubarPrimitive.ItemIndicator>
        <Circle className="h-2 w-2 fill-current" />
      </MenubarPrimitive.ItemIndicator>
    </span>
    {children}
  </MenubarPrimitive.RadioItem>
))
```

**Attributes**:
- `RadioGroup`: Groups related radio items
- `RadioItem`: Individual radio option
  - `className`: Additional CSS classes
  - `children`: Content of the radio item

#### Sub-menu Components

The menubar supports nested menus with the following components:

##### `MenubarSub`

**Purpose**: Container for a sub-menu.

```tsx
function MenubarSub({
  ...props
}: React.ComponentProps<typeof MenubarPrimitive.Sub>) {
  return <MenubarPrimitive.Sub data-slot="menubar-sub" {...props} />
}
```

##### `MenubarSubTrigger`

**Purpose**: Trigger button for opening a sub-menu.

```tsx
const MenubarSubTrigger = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.SubTrigger>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.SubTrigger> & {
    inset?: boolean
  }
>(({ className, inset, children, ...props }, ref) => (
  <MenubarPrimitive.SubTrigger
    ref={ref}
    className={cn(
      "flex cursor-default select-none items-center rounded-sm px-2 py-1.5 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[state=open]:bg-accent data-[state=open]:text-accent-foreground",
      inset && "pl-8",
      className
    )}
    {...props}
  >
    {children}
    <ChevronRight className="ml-auto h-4 w-4" />
  </MenubarPrimitive.SubTrigger>
))
```

**Attributes**:
- `className`: Additional CSS classes
- `inset`: Boolean for left padding alignment
- `children`: Content of the trigger

##### `MenubarSubContent`

**Purpose**: Content container for sub-menu items.

```tsx
const MenubarSubContent = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.SubContent>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.SubContent>
>(({ className, ...props }, ref) => (
  <MenubarPrimitive.SubContent
    ref={ref}
    className={cn(
      "z-50 min-w-[8rem] overflow-hidden rounded-md border bg-popover p-1 text-popover-foreground data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0 data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-95 data-[side=bottom]:slide-in-from-top-2 data-[side=left]:slide-in-from-right-2 data-[side=right]:slide-in-from-left-2 data-[side=top]:slide-in-from-bottom-2",
      className
    )}
    {...props}
  />
))
```

**Attributes**:
- `className`: Additional CSS classes

#### Supporting Components

##### `MenubarLabel`

**Purpose**: A non-interactive label within a menu.

```tsx
const MenubarLabel = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Label>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Label> & {
    inset?: boolean
  }
>(({ className, inset, ...props }, ref) => (
  <MenubarPrimitive.Label
    ref={ref}
    className={cn(
      "px-2 py-1.5 text-sm font-semibold",
      inset && "pl-8",
      className
    )}
    {...props}
  />
))
```

**Attributes**:
- `className`: Additional CSS classes
- `inset`: Boolean for left padding alignment

##### `MenubarSeparator`

**Purpose**: Visual divider between menu items.

```tsx
const MenubarSeparator = React.forwardRef<
  React.ElementRef<typeof MenubarPrimitive.Separator>,
  React.ComponentPropsWithoutRef<typeof MenubarPrimitive.Separator>
>(({ className, ...props }, ref) => (
  <MenubarPrimitive.Separator
    ref={ref}
    className={cn("-mx-1 my-1 h-px bg-muted", className)}
    {...props}
  />
))
```

**Attributes**:
- `className`: Additional CSS classes

##### `MenubarShortcut`

**Purpose**: Displays keyboard shortcut hints next to menu items.

```tsx
const MenubarShortcut = ({
  className,
  ...props
}: React.HTMLAttributes<HTMLSpanElement>) => {
  return (
    <span
      className={cn(
        "ml-auto text-xs tracking-widest text-muted-foreground",
        className
      )}
      {...props}
    />
  )
}
```

**Attributes**:
- `className`: Additional CSS classes
- Standard HTML span attributes

##### Utility Components

- `MenubarGroup`: Groups related menu items
- `MenubarPortal`: Renders content in a portal (outside the DOM hierarchy)

## Usage Example

```tsx
<Menubar>
  <MenubarMenu>
    <MenubarTrigger>File</MenubarTrigger>
    <MenubarContent>
      <MenubarItem>New Tab <MenubarShortcut>⌘T</MenubarShortcut></MenubarItem>
      <MenubarItem>New Window <MenubarShortcut>⌘N</MenubarShortcut></MenubarItem>
      <MenubarSeparator />
      <MenubarSub>
        <MenubarSubTrigger>Share</MenubarSubTrigger>
        <MenubarSubContent>
          <MenubarItem>Email Link</MenubarItem>
          <MenubarItem>Message</MenubarItem>
        </MenubarSubContent>
      </MenubarSub>
      <MenubarSeparator />
      <MenubarCheckboxItem checked={true}>Show Status Bar</MenubarCheckboxItem>
      <MenubarSeparator />
      <MenubarItem>Exit <MenubarShortcut>⌘Q</MenubarShortcut></MenubarItem>
    </MenubarContent>
  </MenubarMenu>
  
  <MenubarMenu>
    <MenubarTrigger>Edit</MenubarTrigger>
    <MenubarContent>
      <MenubarItem>Undo <MenubarShortcut>⌘Z</MenubarShortcut></MenubarItem>
      <MenubarItem>Redo <MenubarShortcut>⇧⌘Z</MenubarShortcut></MenubarItem>
    </MenubarContent>
  </MenubarMenu>
  
  <MenubarMenu>
    <MenubarTrigger>View</MenubarTrigger>
    <MenubarContent>
      <MenubarRadioGroup value="list">
        <MenubarRadioItem value="list">List</MenubarRadioItem>
        <MenubarRadioItem value="grid">Grid</MenubarRadioItem>
      </MenubarRadioGroup>
    </MenubarContent>
  </MenubarMenu>
</Menubar>
```

## Dependencies

- [React](https://react.dev/)
- [@radix-ui/react-menubar](https://www.radix-ui.com/primitives/docs/components/menubar)
- [lucide-react](https://lucide.dev/): For icons like `Check`, `ChevronRight`, and `Circle`
- [`cn` utility](../../../lib/utils.md): For merging class names