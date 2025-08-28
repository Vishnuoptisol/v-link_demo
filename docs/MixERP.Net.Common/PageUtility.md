# PageUtility.cs Documentation

## Overview
`PageUtility.cs` is a utility class that provides common web page functionality for the MixERP application. It includes methods for page navigation, retrieving user IP addresses, executing JavaScript, URL resolution and validation, managing invalid login attempts, and finding controls within the page hierarchy. This class simplifies common web operations throughout the MixERP application.

## Class Documentation

### PageUtility
**Access Modifier:** `public static`  
**Purpose:** Provides utility methods for web page operations in the MixERP application.

## Method Documentation

### RefreshPage
**Access Modifier:** `public static`  
**Purpose:** Refreshes the current page by redirecting to the same URL.

**Parameters:**
- `page` (System.Web.UI.Page): The current page instance.

**Return Type:** `void`

**Description:**
This method redirects the user to the current page URL, effectively refreshing the page. It performs a null check on the page parameter before attempting redirection.

**Example Usage:**
```csharp
// Refresh the current page
PageUtility.RefreshPage(this);
```

### GetUserIPAddress
**Access Modifier:** `public static`  
**Purpose:** Retrieves the IP address of the current user.

**Parameters:** None

**Return Type:** `string`

**Description:**
This method attempts to get the client IP address by first checking the `HTTP_X_FORWARDED_FOR` server variable (which may contain IP addresses from proxy servers) and falls back to the `REMOTE_ADDR` server variable if necessary. If multiple IP addresses are present in the forwarded header, it takes the first one.

**Example Usage:**
```csharp
// Get the current user's IP address
string ipAddress = PageUtility.GetUserIPAddress();
```

### ExecuteJavaScript
**Access Modifier:** `public static`  
**Purpose:** Registers JavaScript to be executed when the page loads.

**Parameters:**
- `key` (string): A unique identifier for the script.
- `javaScript` (string): The JavaScript code to execute.
- `page` (Page): The page where the JavaScript should be executed.

**Return Type:** `void`

**Description:**
This method uses the ASP.NET ScriptManager to register a JavaScript block that will execute when the page loads.

**Example Usage:**
```csharp
// Show an alert when the page loads
PageUtility.ExecuteJavaScript("alertKey", "alert('Hello World!');", this);
```

### ResolveUrl
**Access Modifier:** `public static`  
**Purpose:** Resolves a relative URL to an absolute URL.

**Parameters:**
- `relativeUrl` (string): The relative URL to resolve.

**Return Type:** `string`

**Description:**
This method resolves a relative URL to an absolute URL using the current page context. If no page context is available, it returns the original relative URL.

**Example Usage:**
```csharp
// Convert ~/path/file.aspx to /ApplicationPath/path/file.aspx
string absoluteUrl = PageUtility.ResolveUrl("~/path/file.aspx");
```

### IsLocalUrl
**Access Modifier:** `public static`  
**Purpose:** Determines if a URL points to the same host as the current request.

**Parameters:**
- `url` (Uri): The URL to check.
- `page` (System.Web.UI.Page): The current page.

**Return Type:** `bool`

**Description:**
This method checks if the provided URL points to the same host as the current request. It returns false if the page is null or if an InvalidOperationException occurs during the check.

**Example Usage:**
```csharp
// Check if a URL is local to the current host
Uri targetUrl = new Uri("http://example.com/page.aspx");
bool isLocal = PageUtility.IsLocalUrl(targetUrl, this);
```

### InvalidPasswordAttempts
**Access Modifier:** `public static`  
**Purpose:** Manages a counter for invalid password attempts in the session.

**Parameters:**
- `page` (System.Web.UI.Page): The current page.
- `increment` (int): The value to add to the counter.

**Return Type:** `int`

**Description:**
This method tracks the number of invalid password attempts in the session. It initializes the counter if it doesn't exist or increments it by the specified value.

**Example Usage:**
```csharp
// Increment the invalid password attempt counter by 1
int attempts = PageUtility.InvalidPasswordAttempts(this, 1);
```

### CheckInvalidAttempts
**Access Modifier:** `public static`  
**Purpose:** Checks if the number of invalid password attempts exceeds the configured maximum and redirects to an access denied page if necessary.

**Parameters:**
- `page` (System.Web.UI.Page): The current page.

**Return Type:** `void`

**Description:**
This method compares the current number of invalid password attempts against the maximum allowed attempts configured in the application settings. If the maximum is reached or exceeded, it redirects the user to an access denied page.

**Example Usage:**
```csharp
// Check if too many invalid password attempts have occurred
PageUtility.CheckInvalidAttempts(this);
```

### GetCurrentDomainName
**Access Modifier:** `public static`  
**Purpose:** Gets the current domain name including protocol and port.

**Parameters:** None

**Return Type:** `string`

**Description:**
This method constructs and returns the current domain name including protocol (e.g., http:// or https://), host name, and port number (if not port 80).

**Example Usage:**
```csharp
// Get the current domain name
string domain = PageUtility.GetCurrentDomainName();
// Example result: "https://example.com:8080"
```

### FindControlIterative
**Access Modifier:** `public static`  
**Purpose:** Recursively searches for a control in the control hierarchy.

**Parameters:**
- `root` (Control): The root control to start searching from.
- `id` (string): The ID of the control to find.

**Return Type:** `Control`

**Description:**
This method recursively searches for a control with a specific ID in the control hierarchy, starting from the provided root control. It returns the found control or null if not found.

**Example Usage:**
```csharp
// Find a control with ID "myTextBox" in the page's control hierarchy
TextBox textBox = (TextBox)PageUtility.FindControlIterative(this, "myTextBox");
```

### CleanUrl
**Access Modifier:** `public static`  
**Purpose:** Validates a URL by checking if it's accessible and properly formatted.

**Parameters:**
- `url` (string): The URL to validate.

**Return Type:** `string`

**Description:**
This method validates a URL by ensuring it has the proper HTTP prefix and attempting to make a HEAD request to check if it's accessible. If the URL is not valid or accessible, it returns an empty string. Otherwise, it returns the valid URL.

**Example Usage:**
```csharp
// Validate and clean a URL
string cleanedUrl = PageUtility.CleanUrl("example.com/page");
// If valid, result might be: "http://example.com/page"
// If invalid, result will be an empty string
```

## Inner Class Documentation

### MyClient
**Access Modifier:** `private`  
**Inheritance:** Inherits from `WebClient`  
**Purpose:** A custom WebClient implementation that allows HEAD requests.

#### Properties:
- `HeadOnly` (bool): Determines if requests should be converted from GET to HEAD.

#### Methods:
- **GetWebRequest**
  - **Access Modifier:** `protected override`
  - **Parameters:**
    - `address` (Uri): The URI to request.
  - **Return Type:** `WebRequest`
  - **Description:** Overrides the base method to convert GET requests to HEAD requests when HeadOnly is true.

## Dependencies
This class depends on the following:

- System.Web.UI namespace for web control functionality
- [Conversion.cs](Conversion.cs) for data type conversion operations

## Notes
- The class is part of the `MixERP.Net.Common` namespace, which provides common utilities for the MixERP application.
- All methods are static, meaning they can be called without instantiating the PageUtility class.
- The class contains methods for both server-side operations (like finding controls) and client-side operations (like executing JavaScript).