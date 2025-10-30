# Header.tsx Documentation

## Overview

The `Header.tsx` component is a responsive navigation header for a dashboard application. It provides the main navigation elements, branding, and user profile management features. This component is responsible for displaying the application logo, navigation links to different sections of the application, and a user profile dropdown menu with logout functionality.

## Component Documentation

### Header

#### Purpose
A functional component that renders the application's header with navigation and user profile elements.

#### Dependencies
- React components from Next.js:
  - `Link` from 'next/link'
  - `usePathname` and `useRouter` from 'next/navigation'
- UI components:
  - [`Button`](../ui/button.md) from '@/components/ui/button'
  - [`Avatar`, `AvatarFallback`, `AvatarImage`](../ui/avatar.md) from '@/components/ui/avatar'
  - [`DropdownMenu` and related components](../ui/dropdown-menu.md) from '@/components/ui/dropdown-menu'
- Icons from 'lucide-react': `LayoutDashboard`, `FolderKanban`, `LogOut`
- Utility functions:
  - [`cn`](../../lib/utils.md) from '@/lib/utils'
- Firebase authentication:
  - `signOut` from 'firebase/auth'
  - [`auth`](../../lib/firebase.md) from '@/lib/firebase'
- Custom hooks:
  - `useToast` from '@/hooks/use-toast'

#### Props
This component does not accept any props.

#### Implementation Details

The component uses several React hooks:
- `usePathname()`: To determine the current path for highlighting active navigation items
- `useRouter()`: For programmatic navigation after logout
- `useToast()`: For displaying toast notifications

##### State Management
No explicit state is managed using `useState`. The component relies on hooks for accessing router state and toast notifications.

##### Rendering
The component renders a header element with the following sections:
1. Left section: Contains the logo and main navigation links
   - Logo with OptiSol branding
   - Navigation buttons for Dashboard and SQA Metrics pages
2. Right section: Contains user information and profile dropdown
   - User role and location information
   - Avatar with dropdown menu for user actions

##### Methods

###### handleLogout
```typescript
const handleLogout = async () => {
  try {
    await signOut(auth);
    router.push('/login');
  } catch (error: any) {
    toast({
      variant: 'destructive',
      title: 'Uh oh! Something went wrong.',
      description: error.message,
    });
  }
};
```

**Purpose**: Handles the user logout process by:
1. Signing out the user from Firebase authentication
2. Redirecting to the login page
3. Showing an error toast if logout fails

**Parameters**: None

**Return Value**: Promise<void>

**Example Usage**:
This method is triggered when the user clicks on the "Log out" option in the dropdown menu:
```jsx
<DropdownMenuItem onClick={handleLogout}>
  <LogOut className="mr-2 h-4 w-4" />
  <span>Log out</span>
</DropdownMenuItem>
```

## Usage Example

The Header component is typically used at the top level of the application layout:

```jsx
import { Header } from '@/components/dashboard/Header';

export default function Layout({ children }) {
  return (
    <div>
      <Header />
      <main>{children}</main>
    </div>
  );
}
```

## Related Components

The Header component integrates with several other components in the project:
- [Overview.tsx](./Overview.md) - Likely appears on the Dashboard page that Header links to
- [ProjectsTable.tsx](../projects/ProjectsTable.md) - Likely appears on the SQA Metrics page that Header links to

## Technical Notes

1. The component uses client-side rendering as indicated by the `'use client'` directive at the top.
2. Responsive design is implemented with the navigation menu being hidden on mobile devices and shown on medium and larger screens (`hidden md:flex`).
3. The component uses conditional styling for the navigation buttons based on the current path to highlight the active page.
4. Firebase authentication is used for handling user sessions and logout functionality.