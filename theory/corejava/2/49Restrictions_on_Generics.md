
# Restrictions on Generics in Java

1. **No Primitive Types**: Java generics do not allow the use of primitive types (such as `int`, `char`, `double`, etc.) as type parameters. Instead, you must use their corresponding wrapper classes (e.g., `Integer`, `Character`, `Double`):
   ```java
   // Invalid: public class Box<int> {} 
   public class Box<T> {} // Valid, T can be any reference type
   ```

2. **No Static Context**: You cannot use type parameters in static fields, static methods, or static initializer blocks. This is because static members belong to the class itself, not to any specific instance, and generics are instance-specific:
   ```java
   public class Example<T> {
       // static T item; // Invalid: Cannot use type parameter in static context
   }
   ```

3. **No Runtime Type Information**: Due to type erasure, generic type information is not available at runtime. As a result, you cannot create instances of generic types, perform `instanceof` checks, or create arrays of parameterized types:
   ```java
   // Cannot do: T obj = new T(); // Compile-time error
   // Cannot do: if (item instanceof T) {} // Compile-time error
   ```

4. **No Generic Exceptions**: You cannot declare generic types for exception classes. For example, you cannot create a generic exception type like `public class MyException<T> extends Exception {}`. Exception handling in Java must use concrete types:
   ```java
   // Invalid: public class MyException<T> extends Exception {}
   public class MyException extends Exception {} // Valid
   ```

5. **Bounded Type Restrictions**: When using bounded type parameters (e.g., `<T extends Number>`), you cannot instantiate T or call methods that are not defined in the bounds. This means that you can only use methods available in the specified bounds, limiting the operations you can perform:
   ```java
   public <T extends Number> void process(T number) {
       // T obj = new T(); // Invalid: Cannot instantiate T
       // number.methodNotInNumber(); // Invalid: Cannot call non-existent methods
   }
   ```
