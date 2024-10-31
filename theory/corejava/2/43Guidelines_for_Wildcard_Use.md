
# Guidelines for Wildcard Use in Java

1. **Use Wildcards When the Type is Uncertain**: Wildcards are particularly useful when you are unsure of the exact type that will be passed to a method or when you want to allow a method to operate on multiple types. This flexibility can simplify method signatures and improve code reuse:
   ```java
   public void printItems(List<?> items) {
       for (Object item : items) {
           System.out.println(item);
       }
   }
   ```

2. **Prefer Bounded Wildcards for Read/Write Operations**: When dealing with collections where you need to both read from and write to, use bounded wildcards. Use `<? extends T>` for reading and `<? super T>` for writing, which helps ensure type safety and maintain clarity in your code:
   ```java
   public void addNumber(List<? super Integer> list) {
       list.add(10); // Safe to add Integer
   }
   ```

3. **Limit Wildcard Usage in Method Signatures**: Avoid using wildcards in method signatures unless necessary. They can make code less readable and more complex. Prefer using concrete types when the type is known, as this increases code clarity:
   ```java
   // Instead of using List<?> use List<String> when type is known
   public void processStrings(List<String> strings) {
       // More readable and clear
   }
   ```

4. **Avoid Mixing Wildcards**: Be cautious when mixing wildcards in the same collection or method. This can lead to confusion and may result in compile-time errors. Stick to a consistent approach in your methods to improve maintainability:
   ```java
   // Avoid mixing List<? extends Number> and List<? super Integer>
   public void process(List<? extends Number> nums, List<? super Integer> ints) {
       // Could lead to complex logic and potential issues
   }
   ```

5. **Document Wildcard Usage**: When using wildcards in your APIs or libraries, clearly document the intended usage and any limitations. This will help users of your code understand how to use the wildcards effectively and avoid potential pitfalls:
   ```java
   /**
    * This method accepts a list of any type of objects.
    * @param items A list of items to print, can be of any type.
    */
   public void printItems(List<?> items) { ... }
   ```
