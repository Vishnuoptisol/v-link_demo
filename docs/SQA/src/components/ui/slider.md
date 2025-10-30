# Slider Component Documentation

## Overview
The `slider.tsx` file defines a reusable Slider UI component for the application. It's a React component that wraps the Radix UI slider primitive, providing a customized slider control with visual styling applied through Tailwind CSS classes. The slider can be used for numeric input where users need to select values from a range.

## Component Documentation

### `Slider` Component

#### Purpose
A customized slider control component that allows users to select values from a continuous or discrete range by dragging a handle (thumb) along a track.

#### Implementation Details
- **Component Type**: React Functional Component (using forwardRef)
- **Base Component**: Wraps `@radix-ui/react-slider` primitives
- **Styling Approach**: Uses utility function `cn()` from [`utils.ts`](../../lib/utils.md) to merge Tailwind CSS classes

#### Props
The component accepts all props that can be passed to `SliderPrimitive.Root` from Radix UI, plus:

- `className`: Optional string for additional CSS classes to apply to the slider root
- All other props are forwarded to the underlying Radix UI Slider component

#### Structure
The Slider is composed of three main parts:
1. **Root**: The container for the entire slider component
2. **Track**: The background rail that represents the full range
3. **Range**: The filled portion of the track that shows the selected range
4. **Thumb**: The draggable handle that users interact with

#### Styling
- The slider uses a combination of utility classes for layout and design
- Applies custom background colors using Tailwind's theme variables:
  - `bg-secondary` for the track
  - `bg-primary` for the range
  - Border uses `border-primary` for the thumb
- Includes touch support with `touch-none` and prevents text selection with `select-none`
- Implements focus states and accessibility styling with `focus-visible` classes

#### Accessibility Features
- Uses Radix UI's built-in keyboard navigation and ARIA attributes
- Includes proper focus states with visible ring indicators
- Provides disabled states with appropriate visual indicators

## Usage Example

```tsx
import { Slider } from "@/components/ui/slider";

// Basic usage
<Slider defaultValue={[50]} max={100} step={1} />

// Range slider with multiple thumbs
<Slider defaultValue={[20, 80]} max={100} step={1} />

// With custom styling
<Slider 
  defaultValue={[30]} 
  max={100} 
  step={5}
  className="my-4 w-[300px]" 
/>

// Disabled state
<Slider defaultValue={[50]} max={100} disabled />
```

## Dependencies
- React: Core library for building the component
- [@radix-ui/react-slider](https://www.radix-ui.com/docs/primitives/components/slider): Provides the unstyled slider primitives
- [`utils.ts`](../../lib/utils.md): Provides the `cn()` utility function for class name merging

## Related Components
This slider component is part of the larger UI component library within the application and follows similar patterns to other form controls and input elements.