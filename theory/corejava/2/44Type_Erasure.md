
# Type Erasure in Java

1. **Definition**: Type erasure is a process in Java generics where the compiler removes all type parameters and replaces them with their bounds or `Object` during compilation. This allows for backward compatibility with non-generic code and ensures that generic types do not add overhead at runtime:
   ```java
   public class Box<T> {
       private T item;
   }
   // After type erasure, Box<T> becomes Box<Object>
   ```

2. **Compile-Time Checks**: Type erasure enables compile-time type checks to ensure that generic code is type-safe. However, once the code is compiled, the generic type information is not available at runtime, which limits some type-specific operations:
   ```java
   public void add(Box<T> box) { // T is available at compile time
       // Runtime information about T is erased
   }
   ```

3. **Restrictions**: Due to type erasure, certain operations are not allowed on generic types. For example, you cannot create instances of type parameters, perform instance checks (using `instanceof`), or create arrays of parameterized types:
   ```java
   // Cannot do: T obj = new T(); // Compile-time error
   // Cannot do: if (obj instanceof T) {} // Compile-time error
   ```

4. **Generic Method Signature**: When defining a generic method, the type parameters are also erased in the method signature. This means that method overloading can be impacted if it relies on type parameters since the method signature would be the same after type erasure:
   ```java
   public <T> void display(T item) {} // After erasure, it appears as void display(Object item)
   ```

5. **Wildcards and Type Erasure**: Wildcards also undergo type erasure. For instance, a method that uses `List<? extends Number>` will treat it as `List<Object>` at runtime. This can impact how collections are handled when using wildcards in generics:
   ```java
   public void process(List<? extends Number> list) {
       // At runtime, list is treated as List<Object>
   }
   ```
