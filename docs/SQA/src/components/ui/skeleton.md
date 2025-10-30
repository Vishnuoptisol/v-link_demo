# Skeleton Component Documentation

## Overview
The `Skeleton` component is a user interface element that provides a loading placeholder visualization. It creates a pulsing effect to indicate that content is being loaded, improving the user experience during data fetching or processing operations. This component is part of the UI component library and can be customized through className props.

## Class Documentation

### Skeleton Component
A functional React component that renders a div with animation properties to create a loading skeleton effect.

**Props:**
- `className`: `string` (optional) - Additional CSS classes to apply to the skeleton component
- `...props`: `React.HTMLAttributes<HTMLDivElement>` - All other HTML div attributes

## Method Documentation

### Skeleton Function
The main component function that returns a styled div element with animation properties.

**Access Modifier:** Public (exported)

**Parameters:**
- `{ className, ...props }`: Object containing:
  - `className`: `string` (optional) - CSS class names to be applied to the skeleton
  - `...props`: All other HTML div attributes

**Return Type:** JSX.Element

**Implementation Details:**
1. Receives component props including optional className
2. Uses the [utils.ts](../../lib/utils.md) `cn` utility function to combine default classes with any provided className
3. Applies the combined classes to a div element
4. Spreads any remaining props to the div

**Example Usage:**
```tsx
// Basic usage
<Skeleton className="h-8 w-48" />

// With custom dimensions and properties
<Skeleton className="h-12 w-full mb-2" aria-label="Loading content" />

// For an avatar placeholder
<Skeleton className="h-10 w-10 rounded-full" />
```

## Dependencies
- Imports the `cn` utility function from [`@/lib/utils`](../../lib/utils.md), which is used for conditional class name construction

## Related Components
The Skeleton component is typically used within other components to represent loading states for various UI elements like cards, text blocks, or data tables.