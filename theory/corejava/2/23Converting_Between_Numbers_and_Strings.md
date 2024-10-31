
# Converting Between Numbers and Strings in Java

1. **Converting Numbers to Strings**: You can convert numeric values to strings using the `String.valueOf()` method or by concatenating the number with an empty string. This is useful for formatting numbers for display:
   ```java
   int number = 100;
   String numString = String.valueOf(number); // Using valueOf
   String numString2 = number + ""; // Using concatenation
   ```

2. **Using `Integer.toString()` and `Double.toString()`**: Each wrapper class provides a `toString()` method that converts the number to a string representation. This is helpful when working with specific numeric types:
   ```java
   int intValue = 42;
   String intStr = Integer.toString(intValue); // Converts int to String

   double doubleValue = 3.14;
   String doubleStr = Double.toString(doubleValue); // Converts double to String
   ```

3. **Converting Strings to Numbers**: To convert a string representation of a number back to its numeric type, use the wrapper class's `parseX` methods, such as `Integer.parseInt()`, `Double.parseDouble()`, or `Float.parseFloat()`:
   ```java
   String strNumber = "123";
   int parsedInt = Integer.parseInt(strNumber); // Converts String to int

   String strDouble = "45.67";
   double parsedDouble = Double.parseDouble(strDouble); // Converts String to double
   ```

4. **Handling Exceptions**: When converting strings to numbers, it's important to handle `NumberFormatException`, which may be thrown if the string cannot be parsed into a valid number. Use try-catch blocks to manage potential errors:
   ```java
   try {
       String invalidNumber = "abc";
       int result = Integer.parseInt(invalidNumber); // Throws NumberFormatException
   } catch (NumberFormatException e) {
       System.out.println("Invalid number format: " + e.getMessage());
   }
   ```

5. **Formatting Numbers as Strings**: To format numbers with specific patterns, such as currency or percentages, use the `DecimalFormat` class. This provides control over how numbers are displayed as strings:
   ```java
   import java.text.DecimalFormat;

   DecimalFormat df = new DecimalFormat("#,###.00"); // Format with commas and 2 decimal places
   String formatted = df.format(1234567.89); // Outputs: "1,234,567.89"
   ```
