# Avatar Component Documentation

## Overview

The `avatar.tsx` file implements a versatile Avatar component system for displaying user profile pictures with fallback support. Built using Radix UI's Avatar primitives, this component provides a standardized way to display user avatars throughout the application with consistent styling and behavior. It handles image loading states and provides a fallback display when images fail to load or aren't provided.

The implementation leverages the [utils.ts](../../lib/utils.md) utility library for class name management.

## Component Documentation

### Avatar

#### Purpose
The root component that wraps the avatar content, defining its dimensions and styling.

#### Props
- `className`: Optional string for additional CSS classes
- All other props are passed through to the underlying Radix UI Avatar.Root component

#### Implementation Details
```tsx
const Avatar = React.forwardRef<
  React.ElementRef<typeof AvatarPrimitive.Root>,
  React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Root>
>(({ className, ...props }, ref) => (
  <AvatarPrimitive.Root
    ref={ref}
    className={cn(
      "relative flex h-10 w-10 shrink-0 overflow-hidden rounded-full",
      className
    )}
    {...props}
  />
))
```

The component applies default styling (10rem height/width, rounded shape) while allowing custom classes to be merged using the `cn` utility from [utils.ts](../../lib/utils.md).

### AvatarImage

#### Purpose
Displays the user's image within the Avatar component.

#### Props
- `className`: Optional string for additional CSS classes
- All standard image props are passed through to the underlying Radix UI Avatar.Image component

#### Implementation Details
```tsx
const AvatarImage = React.forwardRef<
  React.ElementRef<typeof AvatarPrimitive.Image>,
  React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Image>
>(({ className, ...props }, ref) => (
  <AvatarPrimitive.Image
    ref={ref}
    className={cn("aspect-square h-full w-full", className)}
    {...props}
  />
))
```

The component ensures the image maintains proper dimensions and aspect ratio within the avatar container.

### AvatarFallback

#### Purpose
Provides a fallback display when the avatar image is not available or fails to load.

#### Props
- `className`: Optional string for additional CSS classes
- All other props are passed through to the underlying Radix UI Avatar.Fallback component

#### Implementation Details
```tsx
const AvatarFallback = React.forwardRef<
  React.ElementRef<typeof AvatarPrimitive.Fallback>,
  React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Fallback>
>(({ className, ...props }, ref) => (
  <AvatarPrimitive.Fallback
    ref={ref}
    className={cn(
      "flex h-full w-full items-center justify-center rounded-full bg-muted",
      className
    )}
    {...props}
  />
))
```

The component provides a centered, properly styled container for fallback content (typically user initials or a placeholder icon).

## Usage Examples

### Basic Avatar with Image

```tsx
import { Avatar, AvatarImage, AvatarFallback } from "@/components/ui/avatar";

export function UserAvatar() {
  return (
    <Avatar>
      <AvatarImage src="https://example.com/user-profile.jpg" alt="User Name" />
      <AvatarFallback>UN</AvatarFallback>
    </Avatar>
  );
}
```

### Avatar with Fallback Only

```tsx
import { Avatar, AvatarFallback } from "@/components/ui/avatar";

export function UserInitialsAvatar({ initials }) {
  return (
    <Avatar>
      <AvatarFallback>{initials}</AvatarFallback>
    </Avatar>
  );
}
```

### Custom Sized Avatar

```tsx
import { Avatar, AvatarImage, AvatarFallback } from "@/components/ui/avatar";

export function LargeUserAvatar() {
  return (
    <Avatar className="h-16 w-16">
      <AvatarImage src="https://example.com/user-profile.jpg" alt="User Name" />
      <AvatarFallback className="text-lg">UN</AvatarFallback>
    </Avatar>
  );
}
```

## Dependencies

- React
- @radix-ui/react-avatar: Provides the accessible avatar primitive components
- [utils.ts](../../lib/utils.md): Provides the `cn` utility for managing class names

## Notes

- The component uses React's `forwardRef` to properly pass refs to the underlying DOM elements
- Proper display names are assigned to each component for better debugging experience
- The component is marked with "use client" directive, indicating it's meant to be used in client-side rendering contexts