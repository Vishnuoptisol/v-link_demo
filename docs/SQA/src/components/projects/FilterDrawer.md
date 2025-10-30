# FilterDrawer Component Documentation

## Overview

The `FilterDrawer` component is a reusable UI element that provides filtering capabilities for projects in the Testing Application. It allows users to filter projects based on compliance percentage and other metrics like category scores, development, and DevOps metrics. The component is designed as a sliding drawer that can be opened and closed, with options to apply or cancel filter selections.

## Component Documentation

### FilterDrawer

#### Purpose
Provides a user interface for filtering projects based on various criteria, primarily compliance percentages.

#### Props
| Name | Type | Description |
|------|------|-------------|
| `onClose` | `() => void` | Callback function to close the filter drawer |
| `onApply` | `() => void` | Callback function to apply selected filters |
| `currentCompliance` | `string` | Current selected compliance percentage filter value |
| `onComplianceChange` | `(value: string) => void` | Callback function when compliance filter changes |

#### Dependencies
- UI Components:
  - [`Button`](../ui/button.md) from '@/components/ui/button'
  - [`Select`, `SelectContent`, `SelectItem`, `SelectTrigger`, `SelectValue`](../ui/select.md) from '@/components/ui/select'
  - [`Input`](../ui/input.md) from '@/components/ui/input'
  - [`Label`](../ui/label.md) from '@/components/ui/label'
  - [`RadioGroup`, `RadioGroupItem`](../ui/radio-group.md) from '@/components/ui/radio-group'
  - [`Separator`](../ui/separator.md) from '../ui/separator'
  - [`Card`](../ui/card.md) from '../ui/card'
- Utilities:
  - [`cn`](../../lib/utils.md) from '@/lib/utils' - Utility for conditionally joining classNames
- External Libraries:
  - `X` icon from 'lucide-react'

## Method Documentation

### handleApplyClick

#### Purpose
Handles the click event when the user applies the selected filters.

#### Access Modifier
Private (function defined within component)

#### Parameters
None

#### Return Type
`void`

#### Logic
1. Calls the `onApply` callback function passed as a prop to apply selected filters
2. Calls the `onClose` callback function to close the drawer

#### Example Usage
```tsx
<Button className="w-full" onClick={handleApplyClick}>
  Apply
</Button>
```

## Component Structure and Behavior

### Constants

#### compliantPercentageOptions
An array of objects defining the available compliance percentage filter options:
- `all`: All compliance percentages
- `0-50`: 0% to 50% compliance (displayed with a red indicator)
- `50-80`: 50% to 80% compliance (displayed with a yellow indicator)
- `80-100`: 80% to 100% compliance (displayed with a green indicator)

### Rendering

The component renders a card with the following sections:

1. **Header**
   - Title: "Filter"
   - Close button with X icon

2. **Filter Options Section**
   - **Compliant Percentage**
     - Radio group with predefined options from `compliantPercentageOptions`
     - Color-coded indicators for different compliance ranges
     - "Or" separator
     - Custom range inputs (From/To fields)
     
   - **Category Score**
     - Dropdown select with predefined score ranges
     
   - **Development**
     - Dropdown select with numeric options
     
   - **DevOps**
     - Dropdown select with numeric options

3. **Action Footer**
   - Cancel button - closes the drawer without applying filters
   - Apply button - applies selected filters and closes the drawer

### Styling

The component uses Tailwind CSS for styling:
- Flexbox layout for proper organization
- Grid layout for radio options and range inputs
- Overflow handling for scrollable content
- Color-coded indicators for compliance ranges
- Responsive design with appropriate spacing

## Usage Example

```tsx
import { FilterDrawer } from '@/components/projects/FilterDrawer';

function ProjectsPage() {
  const [showFilters, setShowFilters] = useState(false);
  const [complianceFilter, setComplianceFilter] = useState('all');
  
  const handleApplyFilters = () => {
    // Apply filters logic here
    console.log('Filters applied with compliance:', complianceFilter);
  };
  
  return (
    <div>
      <Button onClick={() => setShowFilters(true)}>Show Filters</Button>
      
      {showFilters && (
        <FilterDrawer
          onClose={() => setShowFilters(false)}
          onApply={handleApplyFilters}
          currentCompliance={complianceFilter}
          onComplianceChange={setComplianceFilter}
        />
      )}
    </div>
  );
}
```

## Related Components

This component is related to other project filtering components in the application:
- [`ProjectDetailsFilterDrawer`](./ProjectDetailsFilterDrawer.md) - For filtering project details
- [`ComplianceMetricsDrawer`](./ComplianceMetricsDrawer.md) - For displaying compliance metrics
- [`ProjectsTable`](./ProjectsTable.md) - The table that likely uses these filters