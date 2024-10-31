
# Generic Methods in Java

1. **Definition**: Generic methods are methods that introduce their own type parameters. They allow for type-safe operations on different types without requiring multiple method definitions. The type parameters are defined within angle brackets (`<T>`) before the method's return type:
   ```java
   public <T> void printArray(T[] array) {
       for (T element : array) {
           System.out.println(element);
       }
   }
   ```

2. **Type Inference**: When you call a generic method, Java can often infer the type arguments based on the method arguments provided. This means you do not always need to specify the type explicitly, making the code cleaner and easier to read:
   ```java
   Integer[] intArray = {1, 2, 3};
   printArray(intArray); // Type inferred as Integer
   ```

3. **Bounded Type Parameters**: You can restrict the types that can be used as type arguments by using bounded type parameters. This is done using the `extends` keyword, allowing the method to accept only subclasses of a specified class or interface:
   ```java
   public <T extends Number> void processNumber(T number) {
       System.out.println("Processing number: " + number);
   }
   ```

4. **Multiple Type Parameters**: A generic method can have multiple type parameters, allowing for more flexibility in handling different types. Each type parameter is separated by a comma within the angle brackets:
   ```java
   public <T, U> void displayPair(T first, U second) {
       System.out.println("First: " + first + ", Second: " + second);
   }
   ```

5. **Use in Collections**: Generic methods are particularly useful when working with collections. They allow for operations on collections of various types without losing type safety, enabling developers to write more reusable and maintainable code:
   ```java
   public static <E> void addToList(List<E> list, E element) {
       list.add(element); // Safe addition to the list
   }
   ```
