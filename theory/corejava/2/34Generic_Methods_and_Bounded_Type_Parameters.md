
# Generic Methods and Bounded Type Parameters in Java

1. **Combining Generics and Bounds**: Generic methods can have bounded type parameters, which restrict the types that can be passed as arguments to specific classes or interfaces. This allows for more controlled and type-safe operations within the method:
   ```java
   public <T extends Comparable<T>> void sortArray(T[] array) {
       Arrays.sort(array); // Uses the Comparable interface for sorting
   }
   ```

2. **Single Bound Example**: When defining a generic method with a single bounded type parameter, you can specify the bound using the `extends` keyword, ensuring that the type must be a subclass of the specified class or implement the specified interface:
   ```java
   public <T extends Number> void displayNumber(T number) {
       System.out.println("Number: " + number);
   }
   ```

3. **Multiple Bounds**: A generic method can specify multiple bounds, allowing the type to be constrained to subclasses of a specific class and implement one or more interfaces. Multiple bounds are specified using the `&` symbol:
   ```java
   public <T extends Number & Comparable<T>> void compareNumbers(T num1, T num2) {
       System.out.println(num1.compareTo(num2));
   }
   ```

4. **Type Inference with Bounded Generics**: Java's type inference allows the compiler to automatically determine the type parameters based on the method arguments. This simplifies method calls while ensuring type safety:
   ```java
   Integer[] numbers = {1, 2, 3};
   sortArray(numbers); // Type inferred as Integer for T
   ```

5. **Practical Use Cases**: Bounded type parameters in generic methods are particularly useful in scenarios requiring operations that depend on certain behaviors or properties of the type, such as sorting or mathematical computations, enhancing the code's reusability and safety:
   ```java
   public <T extends Number> double sum(T num1, T num2) {
       return num1.doubleValue() + num2.doubleValue(); // Safe arithmetic operation
   }
   ```
