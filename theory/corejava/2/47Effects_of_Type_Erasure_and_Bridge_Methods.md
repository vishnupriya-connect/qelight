
# Effects of Type Erasure and Bridge Methods in Java

1. **Type Erasure**: Type erasure in Java removes all generic type information during compilation. This ensures backward compatibility with non-generic code but results in the loss of specific type information at runtime. Generic types are replaced with their bounds or `Object`:
   ```java
   public class Box<T> {
       private T item;
   }
   // After erasure, Box<T> becomes Box<Object> if no bounds are specified
   ```

2. **Bridge Methods**: To maintain polymorphic behavior in the presence of type erasure, the Java compiler generates bridge methods. These synthetic methods enable subclasses to correctly implement overridden methods in a way that preserves the correct type when using generics:
   ```java
   public class Base<T> {
       public void show(T item) {
           System.out.println(item);
       }
   }

   public class Derived extends Base<String> {
       @Override
       public void show(String item) {
           // Bridge method helps in type compatibility
           System.out.println(item);
       }
   }
   ```

3. **Resolving Ambiguities**: Bridge methods resolve ambiguities that arise due to type erasure, particularly in overridden methods. They allow the Java Virtual Machine (JVM) to call the correct method based on the actual type of the object, maintaining type safety:
   ```java
   public class Base<T> {
       public void show(T item) { ... }
   }

   public class Derived extends Base<Object> {
       @Override
       public void show(Object item) { ... } // Bridge method generated for compatibility
   }
   ```

4. **Performance Implications**: While bridge methods facilitate compatibility, they can introduce slight overhead in terms of performance. However, this overhead is typically negligible and necessary for maintaining the integrity of polymorphism in generic code:
   ```java
   // Bridge methods are synthetic and not directly visible in source code
   ```

5. **Limitations of Type Erasure**: Due to type erasure, certain features are restricted. For example, you cannot perform instance checks on generic types, create instances of type parameters, or use generic types in certain contexts, leading to design considerations when implementing generic classes and methods:
   ```java
   public <T> void createInstance() {
       // T obj = new T(); // Compile-time error: cannot instantiate T
   }
   ```
