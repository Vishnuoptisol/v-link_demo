# Chart Component Documentation

## Overview
The chart component is a comprehensive wrapper around the Recharts library, providing enhanced styling, theming, and utilities for chart visualization in the application. It provides a flexible and customizable way to display data visually with proper theming support for both light and dark modes.

## Dependencies
- React: Used for component creation and hooks
- Recharts: The underlying charting library ([recharts](https://recharts.org/))
- Utility functions from [`utils.ts`](../../lib/utils.md): Used for class name merging

## Class Documentation

### ChartConfig Type
Defines the configuration schema for chart elements.

**Properties**:
- `label`: Optional React node for the label
- `icon`: Optional React component type for the icon
- `color`: Optional string for a single color
- `theme`: Optional record mapping theme names to colors

### ChartContextProps Type
Defines the properties available in the chart context.

**Properties**:
- `config`: The ChartConfig object for the chart

## Components

### ChartContext
**Type**: React Context
**Purpose**: Provides chart configuration to child components

### ChartContainer
**Type**: React ForwardRef Component
**Purpose**: Main container for charts that sets up the styling and context

**Props**:
- `id`: Optional string for chart identification
- `className`: Optional string for additional CSS classes
- `children`: React components to render inside the ResponsiveContainer
- `config`: ChartConfig object for theming and styling
- Additional props spread to the container div

**Example Usage**:
```tsx
<ChartContainer
  config={{
    series1: { color: "#10b981", label: "Revenue" },
    series2: { color: "#f43f5e", label: "Expenses" }
  }}
>
  <LineChart data={data}>
    <Line dataKey="series1" />
    <Line dataKey="series2" />
  </LineChart>
</ChartContainer>
```

### ChartStyle
**Type**: React Component
**Purpose**: Generates CSS variables for chart theming

**Props**:
- `id`: String identifier for the chart
- `config`: ChartConfig object for theming and styling

### ChartTooltip
**Type**: Direct re-export of Recharts Tooltip component
**Purpose**: Provides tooltip functionality in charts

### ChartTooltipContent
**Type**: React ForwardRef Component
**Purpose**: Customized tooltip content for charts

**Props**:
- `active`: Boolean indicating if tooltip is active
- `payload`: Array of data points for the tooltip
- `className`: Optional string for additional CSS classes
- `indicator`: Shape of the indicator ('line', 'dot', or 'dashed'), defaults to 'dot'
- `hideLabel`: Boolean to control label visibility
- `hideIndicator`: Boolean to control indicator visibility
- `label`: Optional label content
- `labelFormatter`: Optional function to format labels
- `labelClassName`: Optional string for label CSS classes
- `formatter`: Optional function to format tooltip content
- `color`: Optional string for tooltip color
- `nameKey`: Optional key to use for name lookups
- `labelKey`: Optional key to use for label lookups

**Example Usage**:
```tsx
<ChartContainer config={config}>
  <LineChart data={data}>
    <Line dataKey="value" />
    <ChartTooltip content={<ChartTooltipContent />} />
  </LineChart>
</ChartContainer>
```

### ChartLegend
**Type**: Direct re-export of Recharts Legend component
**Purpose**: Provides legend functionality in charts

### ChartLegendContent
**Type**: React ForwardRef Component
**Purpose**: Customized legend content for charts

**Props**:
- `className`: Optional string for additional CSS classes
- `hideIcon`: Boolean to control icon visibility
- `payload`: Array of legend items
- `verticalAlign`: Positioning of the legend ('top' or 'bottom')
- `nameKey`: Optional key to use for name lookups

**Example Usage**:
```tsx
<ChartContainer config={config}>
  <BarChart data={data}>
    <Bar dataKey="value" />
    <ChartLegend content={<ChartLegendContent />} />
  </BarChart>
</ChartContainer>
```

## Utility Functions

### useChart
**Purpose**: Hook to access chart configuration from context

**Returns**: ChartContextProps object containing chart config

**Example Usage**:
```tsx
const CustomComponent = () => {
  const { config } = useChart();
  // Use config here
};
```

### getPayloadConfigFromPayload
**Purpose**: Helper function to extract configuration for a specific data point

**Parameters**:
- `config`: ChartConfig object
- `payload`: The data payload object
- `key`: String key to look up in the configuration

**Returns**: Configuration for the specified item or undefined

## Export
The module exports the following components:
- `ChartContainer`
- `ChartTooltip`
- `ChartTooltipContent`
- `ChartLegend`
- `ChartLegendContent`
- `ChartStyle`

And the following type:
- `ChartConfig`

## Usage in the Application
This chart component is used in [`ProjectChart.tsx`](../../components/dashboard/ProjectChart.md) to visualize project-related data in the dashboard.