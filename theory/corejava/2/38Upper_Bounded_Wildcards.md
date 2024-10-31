
# Upper Bounded Wildcards in Java

1. **Definition**: Upper bounded wildcards allow you to specify a type parameter that can be a specific type or any subtype of that type. They are defined using the syntax `<? extends T>`, where T is the upper bound. This provides flexibility while ensuring type safety:
   ```java
   public void processList(List<? extends Number> list) {
       // Can accept List<Integer>, List<Double>, etc.
   }
   ```

2. **Read-Only Access**: When using upper bounded wildcards, you can read items from the collection, treating them as instances of the upper bound type. This allows you to safely perform operations that are applicable to that type and its subclasses:
   ```java
   public void printNumbers(List<? extends Number> numbers) {
       for (Number number : numbers) {
           System.out.println(number); // Safe to use as Number
       }
   }
   ```

3. **Limitations on Writing**: While you can read from a collection with upper bounded wildcards, you cannot add elements to it (except for null). This is because the compiler cannot guarantee that the element you want to add is compatible with the wildcard type:
   ```java
   public void addToList(List<? extends Number> numbers) {
       // numbers.add(10); // Compile-time error: cannot add to the list
   }
   ```

4. **Use Cases**: Upper bounded wildcards are particularly useful in methods that operate on collections of a certain type, allowing for more general handling of multiple subclasses. This is common in APIs and libraries where you want to accept a variety of related types:
   ```java
   public double calculateSum(List<? extends Number> numbers) {
       double sum = 0.0;
       for (Number number : numbers) {
           sum += number.doubleValue(); // Works for any subclass of Number
       }
       return sum;
   }
   ```

5. **Combining with Other Generics**: Upper bounded wildcards can be combined with other generic types to create more complex data structures or methods, allowing for sophisticated type relationships and functionality:
   ```java
   public <T extends Number> void processElements(List<? extends T> elements) {
       for (T element : elements) {
           System.out.println("Element: " + element);
       }
   }
   ```
