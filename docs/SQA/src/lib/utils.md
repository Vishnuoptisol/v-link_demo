# Utils.ts Documentation

## Overview

The `utils.ts` file contains utility functions for handling CSS class name operations in a Next.js application with Tailwind CSS. It provides a convenient way to merge and manage class names with proper precedence using the `clsx` and `tailwind-merge` libraries. This is particularly useful for creating reusable UI components with customizable styling.

## Function Documentation

### cn

```typescript
export function cn(...inputs: ClassValue[]): string
```

#### Purpose
A utility function that combines multiple class values and resolves Tailwind CSS conflicts by merging them with proper specificity handling.

#### Parameters
- `inputs`: `ClassValue[]` - A rest parameter accepting any number of class values. These values can be strings, objects, arrays, or other valid class name representations as defined by the `clsx` library.

#### Return Value
- `string`: A merged string of CSS class names with Tailwind CSS conflicts properly resolved.

#### Dependencies
- Uses the `clsx` function from the `clsx` package to combine class values
- Uses the `twMerge` function from the `tailwind-merge` package to handle Tailwind CSS specificity conflicts

#### Usage Example
```typescript
import { cn } from "../../lib/utils";

// Basic usage with string class names
const className = cn("text-red-500", "bg-blue-100", "p-4");

// Conditional class application
const buttonClass = cn(
  "px-4 py-2 rounded",
  isActive && "bg-blue-500 text-white",
  isDisabled && "opacity-50 cursor-not-allowed"
);

// With Tailwind conflicts (later classes take precedence)
const resolvedClass = cn("text-sm", "text-lg"); // Will result in "text-lg"
```

#### Implementation Details
The function works in two stages:
1. It passes all input class values to `clsx()` to combine them into a single string
2. It then passes the result to `twMerge()` to resolve any Tailwind CSS conflicts

This approach ensures that:
- Conditional classes are handled properly
- Array or object syntax for class names works as expected
- Tailwind utility classes with the same target property follow the expected override behavior

## Usage Context

This utility is widely used throughout the application's component library, particularly in the UI components found in the `src/components/ui/` directory. It allows components to accept className props from consumers while still maintaining their default styling.