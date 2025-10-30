# ComplianceMetricsDrawer Documentation

## Overview

The `ComplianceMetricsDrawer` component is a React component that displays detailed compliance metrics for a project. It renders a card-based drawer with various compliance metrics grouped by categories like Development, DevOps, and Quality Metrics. The component visualizes compliance percentages using color-coded badges that indicate performance levels (red for low, yellow for medium, green for high compliance).

## Class Documentation

### ComplianceMetricsDrawer

A functional React component that renders a drawer displaying detailed compliance metrics for a project.

**Props:**
- `complianceDetail`: An object of type `ComplianceDetail` containing all metrics data for a project
- `onClose`: A function callback that handles the closing of the drawer

## Helper Components and Functions

### MetricGroup

A functional component that renders a group of related compliance metrics.

**Props:**
- `title`: A string representing the title of the metric group
- `metrics`: An array of `ComplianceMetric` objects to be displayed

### getPercentageBadgeClass

A utility function that determines the appropriate CSS class for a compliance metric badge based on the percentage value.

**Parameters:**
- `percentage`: A number representing the compliance percentage

**Returns:**
- A string containing CSS class names for styling the badge

## Method Documentation

### ComplianceMetricsDrawer

**Access:** Public export
**Parameters:**
- `{ complianceDetail, onClose }`: Destructured object containing:
  - `complianceDetail`: Object of type `ComplianceDetail` from [index.ts](../../types/index.md)
  - `onClose`: Function to be called when the drawer is closed

**Returns:** React JSX Element

**Example Usage:**
```tsx
<ComplianceMetricsDrawer
  complianceDetail={{
    projectName: "Project Alpha",
    categoryScore: "A+",
    metricDetails: {
      compliance: 92.5,
      development: [
        { name: "Code Coverage", value: 87 }
      ],
      devops: [
        { name: "CI/CD Pipeline", value: 95 }
      ],
      qualityMetrics: [
        { name: "Bug Rate", value: 92 }
      ]
    }
  }}
  onClose={() => setIsDrawerOpen(false)}
/>
```

**Step-by-step explanation:**
1. The function extracts `metricDetails` from the `complianceDetail` prop
2. It renders a `Card` component containing:
   - A header with project name and close button
   - Summary information including category score and overall compliance percentage
   - Conditional rendering of metric groups for Development, DevOps, and Quality Metrics categories
3. Metric values are displayed with color-coded badges using the `getPercentageBadgeClass` utility function

### MetricGroup

**Access:** Private component
**Parameters:**
- `{ title, metrics }`: Destructured object containing:
  - `title`: String title for the metric group
  - `metrics`: Array of `ComplianceMetric` objects

**Returns:** React JSX Element

**Example Usage:**
```tsx
<MetricGroup
  title="Development"
  metrics={[
    { name: "Code Coverage", value: 87 },
    { name: "Code Quality", value: 92 }
  ]}
/>
```

### getPercentageBadgeClass

**Access:** Private function
**Parameters:**
- `percentage`: A number representing the compliance percentage value

**Returns:** String containing CSS class names

**Example Usage:**
```tsx
<Badge className={getPercentageBadgeClass(87)}>87%</Badge>
```

**Step-by-step explanation:**
1. If percentage is less than 40, returns classes for red (low performance) styling
2. If percentage is less than 80, returns classes for yellow (medium performance) styling
3. Otherwise, returns classes for green (high performance) styling

## Dependencies

- UI Components:
  - [Button](../../components/ui/button.md) from `@/components/ui/button`
  - [Card](../../components/ui/card.md) from `@/components/ui/card`
  - [Badge](../../components/ui/badge.md) from `../ui/badge`
- Icons:
  - `X` from `lucide-react`
- Utility:
  - [cn](../../lib/utils.md) from `@/lib/utils`
- Types:
  - `ComplianceDetail` and `ComplianceMetric` from [index.ts](../../types/index.md)

## Component Structure

The component uses a nested structure:
1. Main `Card` container with a flex column layout
2. Header section with project name and close button
3. Content section with scrollable overflow containing:
   - Summary statistics (Category Score and Compliance Percentage)
   - Metric groups for each category (Development, DevOps, Quality Metrics)
4. Each metric group shows individual metrics with their percentage values in color-coded badges

The component employs responsive design with proper spacing, borders, and color indicators to create an organized and readable metrics dashboard.