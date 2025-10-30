# Carousel Component Documentation

## Overview
This file provides a comprehensive carousel UI component built with React, using the embla-carousel library. It creates a flexible, accessible carousel that can display content in both horizontal and vertical orientations, with navigation controls and keyboard accessibility.

## Dependencies
- React: Used for component creation and hooks
- [embla-carousel-react](https://www.embla-carousel.com/): Powers the core carousel functionality
- Lucide React: Provides arrow icons for navigation buttons
- [@/lib/utils](../../lib/utils.md): Provides utility functions, specifically the `cn` function for class name management
- [@/components/ui/button](./button.md): Used for the navigation controls

## Class Documentation

### Context
- **CarouselContext**: React Context that provides carousel state and functionality to all child components
  - Type: `React.Context<CarouselContextProps | null>`
  - Default: `null`

### Type Definitions
- **CarouselApi**: Type alias for the Embla Carousel API
- **UseCarouselParameters**: Parameters for useEmblaCarousel hook
- **CarouselOptions**: Options for configuring the carousel behavior
- **CarouselPlugin**: Plugins for extending carousel functionality

- **CarouselProps**: Props for the main Carousel component
  - `opts?`: CarouselOptions - Configuration options
  - `plugins?`: CarouselPlugin - Plugins for the carousel
  - `orientation?`: "horizontal" | "vertical" - Direction of carousel movement
  - `setApi?`: (api: CarouselApi) => void - Function to access the carousel API externally

- **CarouselContextProps**: Context provided to child components
  - `carouselRef`: Reference to the carousel DOM element
  - `api`: The Embla Carousel API instance
  - `scrollPrev`: Function to scroll to previous slide
  - `scrollNext`: Function to scroll to next slide
  - `canScrollPrev`: Boolean indicating if there's a previous slide
  - `canScrollNext`: Boolean indicating if there's a next slide
  - Plus all properties from CarouselProps

## Component Documentation

### Carousel
The main wrapper component that initializes the carousel and provides context to children.

**Props:**
- All standard HTMLDivElement props, plus:
  - `orientation`: "horizontal" | "vertical" - Direction of carousel movement (default: "horizontal")
  - `opts`: CarouselOptions - Configuration options for the carousel
  - `plugins`: CarouselPlugin - Plugins for the carousel
  - `setApi`: (api: CarouselApi) => void - Function to externally access the carousel API
  - `className`: String - Additional CSS classes
  - `children`: React.ReactNode - Content to display within the carousel

**Implementation Details:**
- Initializes the embla carousel with the provided options
- Manages scroll state (can scroll prev/next)
- Provides keyboard navigation with left/right arrow keys
- Sets up event listeners for carousel state updates
- Wraps children in the CarouselContext.Provider

**Example Usage:**
```jsx
<Carousel orientation="horizontal">
  <CarouselContent>
    <CarouselItem>Slide 1</CarouselItem>
    <CarouselItem>Slide 2</CarouselItem>
  </CarouselContent>
  <CarouselPrevious />
  <CarouselNext />
</Carousel>
```

### CarouselContent
Container for carousel items that defines the scrollable area.

**Props:**
- All standard HTMLDivElement props, plus:
  - `className`: String - Additional CSS classes

**Implementation Details:**
- Receives the carousel reference from context
- Sets up the overflow container and flex layout based on orientation
- Applies appropriate spacing and layout based on orientation

### CarouselItem
Individual slide within the carousel.

**Props:**
- All standard HTMLDivElement props, plus:
  - `className`: String - Additional CSS classes

**Implementation Details:**
- Sets proper ARIA roles for accessibility
- Applies appropriate spacing based on orientation
- Uses flex basis for equal width/height items

### CarouselPrevious
Navigation button to move to the previous slide.

**Props:**
- All props from [Button](./button.md) component, plus:
  - `variant`: String - Button style variant (default: "outline")
  - `size`: String - Button size (default: "icon")
  - `className`: String - Additional CSS classes

**Implementation Details:**
- Positioned absolutely based on carousel orientation
- Disabled when there's no previous slide to navigate to
- Contains an arrow icon and screen reader text

### CarouselNext
Navigation button to move to the next slide.

**Props:**
- All props from [Button](./button.md) component, plus:
  - `variant`: String - Button style variant (default: "outline")
  - `size`: String - Button size (default: "icon")
  - `className`: String - Additional CSS classes

**Implementation Details:**
- Positioned absolutely based on carousel orientation
- Disabled when there's no next slide to navigate to
- Contains an arrow icon and screen reader text

## Hook Documentation

### useCarousel
Custom hook to access the carousel context within child components.

**Returns:**
- The carousel context (CarouselContextProps)

**Throws:**
- Error if used outside of a Carousel component

**Example Usage:**
```jsx
function MyCarouselComponent() {
  const { scrollNext, canScrollNext } = useCarousel();
  
  return (
    <button onClick={scrollNext} disabled={!canScrollNext}>
      Next Slide
    </button>
  );
}
```

## Accessibility Features
- Proper ARIA roles: "region" for carousel, "group" for items, "slide" for individual items
- ARIA roledescription attributes
- Screen reader text for navigation buttons
- Keyboard navigation support (left/right arrows)

## Exports
- `CarouselApi` type
- `Carousel` component
- `CarouselContent` component
- `CarouselItem` component
- `CarouselPrevious` component
- `CarouselNext` component