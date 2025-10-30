# Card Component Documentation

## Overview

The Card component is a versatile UI element that provides a consistent container layout with a clean, modern design. It's part of the project's UI component library and follows a compound component pattern with six distinct components: `Card`, `CardHeader`, `CardTitle`, `CardDescription`, `CardContent`, and `CardFooter`. This structure allows for flexible content organization within a visually cohesive card interface.

The component utilizes the `cn` utility function from the [`utils.ts`](../../lib/utils.md) library for class name merging, enabling both default styling and custom class application.

## Component Documentation

### Card

#### Purpose
The main container component that wraps all card content and provides the base card styling with border, background, and shadow.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const Card = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn(
      "rounded-lg border bg-card text-card-foreground shadow-sm",
      className
    )}
    {...props}
  />
))
Card.displayName = "Card"
```

#### Usage Example
```tsx
<Card className="w-[350px]">
  {/* Card content */}
</Card>
```

### CardHeader

#### Purpose
Container for the top section of the card, typically containing the title and description.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const CardHeader = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn("flex flex-col space-y-1.5 p-6", className)}
    {...props}
  />
))
CardHeader.displayName = "CardHeader"
```

#### Usage Example
```tsx
<CardHeader>
  <CardTitle>Card Title</CardTitle>
  <CardDescription>Card Description</CardDescription>
</CardHeader>
```

### CardTitle

#### Purpose
Displays the main heading or title of the card with appropriate typography styling.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const CardTitle = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn(
      "text-2xl font-semibold leading-none tracking-tight",
      className
    )}
    {...props}
  />
))
CardTitle.displayName = "CardTitle"
```

#### Usage Example
```tsx
<CardTitle>Account Settings</CardTitle>
```

### CardDescription

#### Purpose
Provides a secondary text area for additional context or explanation below the title.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const CardDescription = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn("text-sm text-muted-foreground", className)}
    {...props}
  />
))
CardDescription.displayName = "CardDescription"
```

#### Usage Example
```tsx
<CardDescription>Manage your account settings and preferences.</CardDescription>
```

### CardContent

#### Purpose
The main content area of the card, with appropriate padding that works with the header and footer components.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const CardContent = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div ref={ref} className={cn("p-6 pt-0", className)} {...props} />
))
CardContent.displayName = "CardContent"
```

#### Usage Example
```tsx
<CardContent>
  <p>Main content goes here</p>
</CardContent>
```

### CardFooter

#### Purpose
Container for the bottom section of the card, typically used for action buttons or secondary information.

#### Attributes
- `className`: Optional string for additional CSS classes
- All other HTML div attributes via `...props` spread

#### Implementation
```tsx
const CardFooter = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn("flex items-center p-6 pt-0", className)}
    {...props}
  />
))
CardFooter.displayName = "CardFooter"
```

#### Usage Example
```tsx
<CardFooter>
  <Button>Save Changes</Button>
</CardFooter>
```

## Complete Card Component Usage Example

```tsx
<Card className="w-[350px]">
  <CardHeader>
    <CardTitle>Project Overview</CardTitle>
    <CardDescription>Summary of your current project status</CardDescription>
  </CardHeader>
  <CardContent>
    <p>View details about your project progress and team activity.</p>
  </CardContent>
  <CardFooter>
    <Button>View Details</Button>
  </CardFooter>
</Card>
```

## Dependencies

- React: Used for creating the functional components with `forwardRef`
- [`cn` function from utils.ts](../../lib/utils.md): Utility for merging class names with Tailwind CSS

This component is designed to work seamlessly with other UI components in the system and can be customized through additional class names or by passing HTML div attributes.