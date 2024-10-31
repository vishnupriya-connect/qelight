
# Erasure of Generic Types in Java

1. **Concept of Type Erasure**: In Java, generic types undergo a process called type erasure during compilation, where all type parameters are removed and replaced with their bounds or `Object`. This ensures that generic types remain compatible with older versions of Java that do not support generics:
   ```java
   public class Container<T> {
       private T item;
   }
   // After erasure, Container<T> becomes Container<Object>
   ```

2. **Compile-Time Type Safety**: Type erasure allows the compiler to perform type checks at compile time. This means that generic classes and methods are checked for type correctness during compilation, but the specific type information is not retained at runtime:
   ```java
   public void add(Container<T> container) { // T is known at compile time
       // No type information about T at runtime
   }
   ```

3. **Limitations on Generic Operations**: Due to type erasure, certain operations are restricted. For example, you cannot create instances of generic types, perform instance checks, or create arrays of generic types. This is because the runtime does not have the type information:
   ```java
   // Cannot do: T instance = new T(); // Compile-time error
   // Cannot do: if (obj instanceof T) {} // Compile-time error
   ```

4. **Method Overloading and Type Erasure**: When defining overloaded methods that use generics, the method signatures can become ambiguous after type erasure. This is because different generic type parameters may result in the same method signature at runtime:
   ```java
   public <T> void display(T item) {}
   public <T> void display(List<T> list) {}
   // Both methods will appear as display(Object item) after erasure
   ```

5. **Wildcards and Type Erasure**: Wildcards, such as `?`, also undergo type erasure. For instance, a method with a parameter of type `List<? extends Number>` will treat it as `List<Object>` at runtime, which can affect how collections are handled and what operations can be performed:
   ```java
   public void process(List<? extends Number> list) {
       // At runtime, list is treated as List<Object>
   }
   ```
