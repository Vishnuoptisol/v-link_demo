# DateHelper.cs Documentation

## Overview
`DateHelper.cs` is a utility class in the MixERP.Net.Common library that provides helper methods for date manipulation. This class offers static methods to determine the first and last dates of a given month, simplifying common date operations required throughout the application.

## Class Documentation

### DateHelper
```csharp
public static class DateHelper
```

This is a static utility class containing date-related helper methods. Being static, it cannot be instantiated and all its methods must be accessed through the class name directly.

## Method Documentation

### GetMonthStartDate
```csharp
public static DateTime GetMonthStartDate(DateTime date)
```

#### Description
Calculates the first day of the month for a given date.

#### Access Modifier
- `public`: Accessible from any code that references the assembly.
- `static`: Called directly on the class without creating an instance.

#### Parameters
- `date` (DateTime): The input date from which to determine the first day of its month.

#### Return Type
- `DateTime`: A new DateTime object representing the first day of the month (with time component set to 00:00:00).

#### Implementation Details
The method creates a new DateTime object using the year and month from the input date, but sets the day component to 1, which is always the first day of any month.

#### Example Usage
```csharp
DateTime someDate = new DateTime(2023, 8, 15);  // August 15, 2023
DateTime firstDayOfMonth = DateHelper.GetMonthStartDate(someDate);  // August 1, 2023
```

### GetMonthEndDate
```csharp
public static DateTime GetMonthEndDate(DateTime date)
```

#### Description
Calculates the last day of the month for a given date.

#### Access Modifier
- `public`: Accessible from any code that references the assembly.
- `static`: Called directly on the class without creating an instance.

#### Parameters
- `date` (DateTime): The input date from which to determine the last day of its month.

#### Return Type
- `DateTime`: A new DateTime object representing the last day of the month (with time component set to 00:00:00).

#### Implementation Details
The method uses `DateTime.DaysInMonth(year, month)` to determine how many days are in the specified month, then creates a new DateTime with that day number.

#### Example Usage
```csharp
DateTime someDate = new DateTime(2023, 8, 15);  // August 15, 2023
DateTime lastDayOfMonth = DateHelper.GetMonthEndDate(someDate);  // August 31, 2023
```

## Dependencies
This class has no direct dependencies on other project files beyond standard .NET libraries. It uses the following namespaces:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Note that while `System.Collections.Generic`, `System.Linq`, and `System.Text` are included, they are not actually used within the class implementation.

## Usage Context
These date helper methods may be utilized in various parts of the MixERP application, particularly in:

- Financial reporting where month boundaries are important
- Period calculations for transactions
- Date range selections in user interfaces
- Filtering data by monthly periods

The DateHelper class follows the utility pattern by offering focused, reusable functionality without maintaining any state.