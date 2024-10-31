
# Beyond Basic Arithmetic in Java

1. **Mathematical Functions**: Java's `Math` class provides a variety of mathematical functions beyond basic arithmetic, including trigonometric functions, logarithms, and exponential functions. Some commonly used methods are:
   - `Math.sin(double a)`: Returns the sine of the specified angle.
   - `Math.log(double a)`: Returns the natural logarithm (base e) of a specified number.
   - `Math.exp(double a)`: Returns Euler's number raised to the power of the specified number.
   ```java
   double angle = 30.0;
   double radians = Math.toRadians(angle);
   System.out.println("Sin: " + Math.sin(radians)); // Sin: 0.49999999999999994
   ```

2. **Rounding Methods**: The `Math` class offers several methods for rounding numbers, such as:
   - `Math.round(float a)`: Rounds the floating-point number to the nearest integer.
   - `Math.ceil(double a)`: Returns the smallest integer greater than or equal to the specified number.
   - `Math.floor(double a)`: Returns the largest integer less than or equal to the specified number.
   ```java
   System.out.println(Math.round(2.5)); // Outputs: 3
   System.out.println(Math.ceil(2.1));   // Outputs: 3.0
   System.out.println(Math.floor(2.9));  // Outputs: 2.0
   ```

3. **Random Number Generation**: The `java.util.Random` class provides methods for generating random numbers. This is useful for simulations, games, and applications requiring unpredictability:
   ```java
   import java.util.Random;

   Random rand = new Random();
   int randomInt = rand.nextInt(100); // Random integer between 0 and 99
   double randomDouble = rand.nextDouble(); // Random double between 0.0 and 1.0
   ```

4. **BigDecimal for Precision**: For precise calculations, especially in financial applications, use the `BigDecimal` class. It allows for arbitrary-precision arithmetic and avoids issues with floating-point precision:
   ```java
   import java.math.BigDecimal;

   BigDecimal price = new BigDecimal("19.99");
   BigDecimal quantity = new BigDecimal("3");
   BigDecimal total = price.multiply(quantity); // Accurate multiplication
   System.out.println("Total: " + total); // Outputs: Total: 59.97
   ```

5. **Complex Numbers**: While Java does not have a built-in complex number class, you can create one using a custom class to handle complex arithmetic (addition, subtraction, multiplication, etc.) or use third-party libraries like Apache Commons Math for complex number support:
   ```java
   class Complex {
       private double real;
       private double imaginary;

       public Complex(double real, double imaginary) {
           this.real = real;
           this.imaginary = imaginary;
       }

       public Complex add(Complex other) {
           return new Complex(this.real + other.real, this.imaginary + other.imaginary);
       }
   }
   ```
