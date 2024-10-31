
# Formatting Numeric Print Output in Java

1. **Using `printf` Method**: The `printf` method from the `PrintStream` class (e.g., `System.out`) allows formatted output similar to the C programming language. It uses format specifiers to define how the output should be formatted:
   ```java
   System.out.printf("Value: %.2f
", 123.456); // Outputs: Value: 123.46
   ```

2. **Format Specifiers**: Common format specifiers include:
   - `%d`: Integer (decimal)
   - `%f`: Floating-point (default 6 decimal places)
   - `%.2f`: Floating-point with 2 decimal places
   - `%s`: String
   - `%n`: Platform-independent newline character
   ```java
   System.out.printf("Integer: %d, Float: %.2f, String: %s%n", 10, 15.678, "Hello");
   ```

3. **Using `DecimalFormat` Class**: The `DecimalFormat` class provides a way to format decimal numbers with specific patterns. This is useful for custom formatting, such as currency or percentage representation:
   ```java
   import java.text.DecimalFormat;

   DecimalFormat df = new DecimalFormat("#,###.##");
   System.out.println(df.format(1234567.89)); // Outputs: 1,234,567.89
   ```

4. **Currency Formatting**: You can format numbers as currency using `NumberFormat`. This class provides methods for formatting currency according to the default locale or a specific locale:
   ```java
   import java.text.NumberFormat;
   import java.util.Locale;

   NumberFormat currencyFormatter = NumberFormat.getCurrencyInstance(Locale.US);
   System.out.println(currencyFormatter.format(1234.56)); // Outputs: $1,234.56
   ```

5. **Percent Formatting**: To format numbers as percentages, you can use `NumberFormat.getPercentInstance()`. This formats a number as a percentage, multiplying it by 100 and appending a percent sign:
   ```java
   NumberFormat percentFormatter = NumberFormat.getPercentInstance();
   System.out.println(percentFormatter.format(0.75)); // Outputs: 75%
   ```
