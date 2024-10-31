
# Generics in Java

1. **Definition**: Generics allow you to define classes, interfaces, and methods with a placeholder for types (known as type parameters). This enables stronger type checks at compile time and eliminates the need for casting when using collections:
   ```java
   public class Box<T> {
       private T item;

       public void setItem(T item) {
           this.item = item;
       }

       public T getItem() {
           return item;
       }
   }
   ```

2. **Type Safety**: Generics provide type safety by allowing you to specify the exact type of objects that a collection can hold. This helps prevent `ClassCastException` at runtime by ensuring that only the specified type can be added to the collection:
   ```java
   Box<String> stringBox = new Box<>();
   stringBox.setItem("Hello"); // Safe to add a String
   // stringBox.setItem(123); // Compile-time error
   ```

3. **Wildcards**: Generics support wildcards (`?`) that allow for more flexible type parameters. Common wildcard uses include:
   - **Unbounded Wildcard**: `?` can represent any type.
   - **Upper Bounded Wildcard**: `<? extends Type>` restricts the unknown type to be a subtype of `Type`.
   - **Lower Bounded Wildcard**: `<? super Type>` restricts the unknown type to be a supertype of `Type`:
   ```java
   public void printBox(Box<? extends Number> box) {
       System.out.println(box.getItem());
   }
   ```

4. **Generic Methods**: You can define generic methods that work with different types. The type parameter is defined before the return type of the method. This allows for methods that are more flexible and reusable:
   ```java
   public static <T> void printArray(T[] array) {
       for (T element : array) {
           System.out.println(element);
       }
   }
   ```

5. **Type Erasure**: Java implements generics using a process called type erasure, which removes all generic type information during compilation. This means that generic types are replaced with their bounds or `Object` if no bounds are specified. While this allows for backward compatibility, it limits certain operations, such as creating instances of type parameters:
   ```java
   // Cannot do: T obj = new T(); // Compile-time error due to type erasure
   ```
