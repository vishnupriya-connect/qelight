
# Numbers in Java

1. **Primitive Data Types**: Java provides several primitive data types for representing numbers. The main numeric types are:
   - **int**: A 32-bit signed integer, ranging from -2^31 to 2^31-1.
   - **double**: A 64-bit double-precision floating-point number for representing decimal values.
   - **float**: A 32-bit single-precision floating-point number (less commonly used than double).
   ```java
   int age = 30;
   double salary = 50000.50;
   ```

2. **Wrapper Classes**: Each primitive numeric type has a corresponding wrapper class that provides methods for converting between types, manipulating numbers, and performing operations. For example:
   - **Integer** for `int`
   - **Double** for `double`
   - **Float** for `float`
   ```java
   Integer num = Integer.valueOf(age); // Boxing
   int primitiveNum = num.intValue();   // Unboxing
   ```

3. **Arithmetic Operations**: Java supports basic arithmetic operations such as addition, subtraction, multiplication, and division. Arithmetic operators include `+`, `-`, `*`, and `/`. Be aware of integer division, which truncates decimal values:
   ```java
   int result = 10 / 3; // result is 3, not 3.333...
   ```

4. **Math Class**: The `Math` class provides various static methods for performing mathematical operations, such as finding square roots, calculating powers, and trigonometric functions. It also includes constants like `Math.PI` and `Math.E`:
   ```java
   double squareRoot = Math.sqrt(16); // Returns 4.0
   double power = Math.pow(2, 3);      // Returns 8.0
   ```

5. **BigDecimal for Precision**: For applications that require precise decimal representation, such as financial calculations, Java provides the `BigDecimal` class. It allows for arbitrary-precision arithmetic and avoids issues with floating-point precision:
   ```java
   import java.math.BigDecimal;

   BigDecimal price = new BigDecimal("19.99");
   BigDecimal quantity = new BigDecimal("5");
   BigDecimal total = price.multiply(quantity); // Multiplication without precision loss
   ```
