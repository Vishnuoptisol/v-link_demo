# MixERP.Net.Common.Conversion

## Overview

The `Conversion` class in MixERP.Net.Common provides a comprehensive set of utility methods for type conversion and data transformation. It offers safe conversion methods between various data types, hashing functionality for passwords, and utilities for handling dates, images, and collections. This static class serves as a core utility component within the MixERP framework, providing reliable data conversion operations while preventing exceptions from propagating to calling code.

## Class Documentation

### Conversion

`public static class Conversion`

A static utility class that provides various data conversion methods for handling different data types safely.

## Method Documentation

### MapPathReverse

```csharp
public static string MapPathReverse(string fullServerPath)
```

**Description**: Converts a physical server path to a web application relative path.

**Access Modifier**: `public static`

**Parameters**:
- `fullServerPath` (string): The full physical path on the server.

**Return Type**: `string` - A web application relative path (starting with "~/").

**Example Usage**:
```csharp
string physicalPath = "C:\\inetpub\\wwwroot\\myapp\\images\\logo.png";
string relativePath = Conversion.MapPathReverse(physicalPath);
// Returns: "~/images/logo.png"
```

### TryCastShort

```csharp
public static short TryCastShort(object value)
```

**Description**: Attempts to convert an object to a short (Int16) value. Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to short.

**Return Type**: `short` - The converted short value or 0 if conversion fails.

**Example Usage**:
```csharp
short number = Conversion.TryCastShort("123");
// Returns: 123
```

### TryCastLong

```csharp
public static long TryCastLong(object value)
```

**Description**: Attempts to convert an object to a long (Int64) value. Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to long.

**Return Type**: `long` - The converted long value or 0 if conversion fails.

**Example Usage**:
```csharp
long number = Conversion.TryCastLong("9876543210");
// Returns: 9876543210
```

### TryCastSingle

```csharp
public static float TryCastSingle(object value)
```

**Description**: Attempts to convert an object to a float (Single) value. Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to float.

**Return Type**: `float` - The converted float value or 0 if conversion fails.

**Example Usage**:
```csharp
float number = Conversion.TryCastSingle("123.45");
// Returns: 123.45
```

### TryCastDouble

```csharp
public static double TryCastDouble(object value)
```

**Description**: Attempts to convert an object to a double value. Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to double.

**Return Type**: `double` - The converted double value or 0 if conversion fails.

**Example Usage**:
```csharp
double number = Conversion.TryCastDouble("123.4567");
// Returns: 123.4567
```

### TryCastInteger

```csharp
public static int TryCastInteger(object value)
```

**Description**: Attempts to convert an object to an integer (Int32) value. Special handling for boolean values (true = 1, false = 0). Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to integer.

**Return Type**: `int` - The converted integer value or 0 if conversion fails.

**Example Usage**:
```csharp
int number = Conversion.TryCastInteger("456");
// Returns: 456

int boolAsInt = Conversion.TryCastInteger(true);
// Returns: 1
```

### TryCastDate

```csharp
public static DateTime TryCastDate(object value)
```

**Description**: Attempts to convert an object to a DateTime value. Returns DateTime.MinValue if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to DateTime.

**Return Type**: `DateTime` - The converted DateTime value or DateTime.MinValue if conversion fails.

**Example Usage**:
```csharp
DateTime date = Conversion.TryCastDate("2023-08-15");
// Returns: DateTime representing August 15, 2023
```

### TryCastDecimal

```csharp
public static decimal TryCastDecimal(object value)
```

**Description**: Attempts to convert an object to a decimal value. Returns 0 if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to decimal.

**Return Type**: `decimal` - The converted decimal value or 0 if conversion fails.

**Example Usage**:
```csharp
decimal number = Conversion.TryCastDecimal("123.45");
// Returns: 123.45M
```

### TryCastBoolean

```csharp
public static bool TryCastBoolean(object value)
```

**Description**: Attempts to convert an object to a boolean value. Special handling for strings "yes" and "true". Returns false if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to boolean.

**Return Type**: `bool` - The converted boolean value or false if conversion fails.

**Example Usage**:
```csharp
bool result1 = Conversion.TryCastBoolean("true");
// Returns: true

bool result2 = Conversion.TryCastBoolean("yes");
// Returns: true

bool result3 = Conversion.TryCastBoolean("false");
// Returns: false
```

### IsNumeric

```csharp
public static bool IsNumeric(string value)
```

**Description**: Determines if a string value can be parsed as a numeric value.

**Access Modifier**: `public static`

**Parameters**:
- `value` (string): The string to check.

**Return Type**: `bool` - True if the string can be parsed as a number, otherwise false.

**Example Usage**:
```csharp
bool isNumber = Conversion.IsNumeric("123.45");
// Returns: true

bool isNotNumber = Conversion.IsNumeric("abc");
// Returns: false
```

### TryCastString

```csharp
public static string TryCastString(object value)
```

**Description**: Attempts to convert an object to a string value. Special handling for boolean values ("true"/"false") and DBNull. Returns empty string if conversion fails.

**Access Modifier**: `public static`

**Parameters**:
- `value` (object): The object to convert to string.

**Return Type**: `string` - The converted string value or empty string if conversion fails.

**Example Usage**:
```csharp
string result1 = Conversion.TryCastString(true);
// Returns: "true"

string result2 = Conversion.TryCastString(123);
// Returns: "123"

string result3 = Conversion.TryCastString(DBNull.Value);
// Returns: ""
```

### HashSha512

```csharp
public static string HashSha512(string password, string salt)
```

**Description**: Creates a SHA-512 hash from a password and salt combination.

**Access Modifier**: `public static`

**Parameters**:
- `password` (string): The password to hash.
- `salt` (string): The salt value to add to the password.

**Return Type**: `string` - The Base64 encoded SHA-512 hash of the password and salt.

**Example Usage**:
```csharp
string hash = Conversion.HashSha512("MyPassword", "MySalt");
// Returns: Base64 encoded SHA-512 hash
```

### GetBackEndUrl

```csharp
public static Uri GetBackEndUrl(System.Web.HttpContext context, string relativePath)
```

**Description**: Constructs a backend URL based on the HTTP context and relative path, taking into account internationalization settings.

**Access Modifier**: `public static`

**Parameters**:
- `context` (HttpContext): The current HTTP context.
- `relativePath` (string): The relative path to append to the backend URL.

**Return Type**: `Uri` - An absolute URI to the backend resource.

**Example Usage**:
```csharp
Uri backendUrl = Conversion.GetBackEndUrl(HttpContext.Current, "reports");
// Returns: URI like "http://domain.com:80/myapp/administration/en/reports/"
```

### GetLocalDateTime

```csharp
public static DateTime GetLocalDateTime(string timeZone, DateTime utc)
```

**Description**: Converts a UTC DateTime to a local DateTime based on the specified time zone.

**Access Modifier**: `public static`

**Parameters**:
- `timeZone` (string): The time zone ID (e.g., "Eastern Standard Time").
- `utc` (DateTime): The UTC DateTime to convert.

**Return Type**: `DateTime` - The local DateTime based on the specified time zone.

**Example Usage**:
```csharp
DateTime localTime = Conversion.GetLocalDateTime("Eastern Standard Time", DateTime.UtcNow);
// Returns: Current local time in Eastern Standard Time
```

### GetLocalDateTimeString

```csharp
public static string GetLocalDateTimeString(string timeZone, DateTime utc)
```

**Description**: Converts a UTC DateTime to a formatted local date and time string based on the specified time zone.

**Access Modifier**: `public static`

**Parameters**:
- `timeZone` (string): The time zone ID (e.g., "Eastern Standard Time").
- `utc` (DateTime): The UTC DateTime to convert.

**Return Type**: `string` - A formatted string with the local date, time, and time zone display name.

**Example Usage**:
```csharp
string localTimeString = Conversion.GetLocalDateTimeString("Eastern Standard Time", DateTime.UtcNow);
// Returns: "Monday, August 15, 2023 10:30:45 AM (UTC-05:00) Eastern Time (US & Canada)"
```

### TryCastByteArray (Bitmap)

```csharp
public static byte[] TryCastByteArray(Bitmap bitmap)
```

**Description**: Converts a Bitmap object to a byte array.

**Access Modifier**: `public static`

**Parameters**:
- `bitmap` (Bitmap): The Bitmap to convert.

**Return Type**: `byte[]` - The byte array representation of the bitmap.

**Example Usage**:
```csharp
Bitmap image = new Bitmap("logo.png");
byte[] imageData = Conversion.TryCastByteArray(image);
// Returns: byte array containing the image data
```

### TryCastByteArray (Image)

```csharp
public static byte[] TryCastByteArray(Image image)
```

**Description**: Converts an Image object to a byte array.

**Access Modifier**: `public static`

**Parameters**:
- `image` (Image): The Image to convert.

**Return Type**: `byte[]` - The byte array representation of the image.

**Example Usage**:
```csharp
Image image = Image.FromFile("photo.jpg");
byte[] imageData = Conversion.TryCastByteArray(image);
// Returns: byte array containing the image data
```

### ConvertListToDataTable

```csharp
public static System.Data.DataTable ConvertListToDataTable<T>(System.Collections.Generic.IList<T> list)
```

**Description**: Converts a generic list to a DataTable, preserving property names and types.

**Access Modifier**: `public static`

**Parameters**:
- `list` (IList<T>): The generic list to convert.

**Return Type**: `DataTable` - A DataTable representation of the list.

**Example Usage**:
```csharp
List<Customer> customers = GetCustomers();
DataTable customerTable = Conversion.ConvertListToDataTable(customers);
// Returns: DataTable with columns matching Customer properties
```

### ConvertImageToByteArray

```csharp
public static byte[] ConvertImageToByteArray(System.Drawing.Image imageToConvert, System.Drawing.Imaging.ImageFormat formatOfImage)
```

**Description**: Converts an Image to a byte array using the specified image format.

**Access Modifier**: `public static`

**Parameters**:
- `imageToConvert` (Image): The Image to convert.
- `formatOfImage` (ImageFormat): The format to use when converting (e.g., JPEG, PNG).

**Return Type**: `byte[]` - The byte array representation of the image in the specified format.

**Example Usage**:
```csharp
Image photo = Image.FromFile("photo.jpg");
byte[] jpegData = Conversion.ConvertImageToByteArray(photo, ImageFormat.Jpeg);
// Returns: byte array containing the JPEG image data
```

## Dependencies

This class depends on several .NET system namespaces as well as the following MixERP components:
- [Parameters.cs](MixERP.Net.Common/Helpers/Parameters.md) (commented out in the code)

## Notes

- Several methods in this class provide "safe" type conversion by catching and suppressing exceptions.
- The code contains a commented-out `RemoveGroupping` method that would handle number formatting with culture-specific separators.
- The `HashSha512` method uses the SHA-512 algorithm for secure password hashing when combined with a salt.
- The `GetBackEndUrl` method constructs URLs taking into account application paths, language settings, and security protocols.