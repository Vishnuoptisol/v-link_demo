# ExpressionHelper Documentation

## Overview

The `ExpressionHelper` class provides functionality to dynamically evaluate C# expressions at runtime using the .NET CodeDOM capabilities. This powerful utility allows executing string expressions as C# code, making it useful for scenarios like rule engines, custom expression evaluation, or dynamic calculations within the MixERP application.

Located in the `MixERP.Net.Common.Helpers` namespace, this helper class offers a simple interface to process string expressions and return their evaluated results.

## Class Documentation

### ExpressionHelper

```csharp
public static class ExpressionHelper
```

**Type**: Static Class  
**Access Modifier**: Public  
**Namespace**: MixERP.Net.Common.Helpers

A utility class that provides methods for runtime evaluation of C# expressions.

## Method Documentation

### Eval

```csharp
public static string Eval(string expression)
```

**Access Modifier**: Public  
**Return Type**: string - The evaluated result of the expression as a string, or empty string if evaluation fails  
**Parameters**:
- `expression` (string): The C# expression to be evaluated

#### Description

The `Eval` method dynamically compiles and executes C# expressions at runtime. It works by:

1. Creating a temporary C# class with a method that returns the result of the provided expression
2. Compiling this code on-the-fly using the C# code provider
3. Executing the compiled code and returning the result as a string

The method includes several common .NET framework references to support a wide range of expressions:
- system.dll
- system.xml.dll
- system.data.dll
- system.windows.forms.dll
- system.drawing.dll

If compilation fails or the expression is invalid, an empty string is returned.

#### Implementation Details

1. Creates a new CSharpCodeProvider within a using block
2. Sets up CompilerParameters with necessary assembly references
3. Builds a C# source code snippet that wraps the expression in a class and method
4. Attempts to compile the generated code
5. If compilation succeeds, creates an instance of the compiled class and invokes the method
6. Returns the result as a string
7. Handles NotImplementedException and compilation errors by returning an empty string

#### Example Usage

```csharp
// Calculate a simple mathematical expression
string result = ExpressionHelper.Eval("5 * 10 + 2");
// result equals "52"

// Format a date
string formattedDate = ExpressionHelper.Eval("DateTime.Now.ToString(\"yyyy-MM-dd\")");
// result equals today's date in "yyyy-MM-dd" format

// Determine if a value is within range
string isInRange = ExpressionHelper.Eval("(10 > 5 && 10 < 20).ToString()");
// result equals "True"
```

#### Dependencies

This class relies on the following .NET framework components:
- System.CodeDom.Compiler
- Microsoft.CSharp
- System.Reflection

## Related Files

This class doesn't appear to have direct dependencies on other files from the MixERP project, but it could be used by various components in the application that need to evaluate dynamic expressions.

## Error Handling

The class implements basic error handling:
- Compilation errors result in returning an empty string
- NotImplementedException is caught and results in returning an empty string
- Other runtime exceptions during expression evaluation are not explicitly handled and would propagate to the caller

## Security Considerations

**Important**: The `Eval` method executes arbitrary C# code at runtime. In a production environment, this should be used with caution and only with trusted input, as it could potentially allow code injection if used with user-provided expressions.