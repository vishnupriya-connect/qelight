
# Generics, Inheritance, and Subtypes in Java

1. **Generic Class Inheritance**: When a generic class extends another generic class, it can inherit the type parameters of the superclass. This allows for the creation of specialized subclasses that maintain type safety across different levels of the class hierarchy:
   ```java
   public class Box<T> {
       private T item;
   }

   public class StringBox extends Box<String> {
       // Inherits the generic type parameter T as String
   }
   ```

2. **Type Parameters in Subclasses**: A subclass can also introduce its own type parameters, effectively creating a new level of generics. This allows subclasses to be more flexible and reusable, while still adhering to the type constraints defined in the superclass:
   ```java
   public class Pair<K, V> {
       private K key;
       private V value;
   }

   public class TypedPair<K> extends Pair<K, String> {
       // K is a type parameter for the key, String is fixed for the value
   }
   ```

3. **Bounded Type Parameters with Inheritance**: You can use bounded type parameters in generic classes and their subclasses. This allows you to specify constraints on the types that can be used, ensuring that only types that meet certain criteria can be instantiated:
   ```java
   public class NumberBox<T extends Number> {
       private T number;
   }

   public class IntegerBox extends NumberBox<Integer> {
       // IntegerBox is constrained to Integer type
   }
   ```

4. **Covariance and Contravariance**: In Java generics, covariance allows you to use a more specific type than originally specified, which can be achieved through wildcards. For example, `List<? extends Number>` allows a list of any subtype of `Number`:
   ```java
   public void processNumbers(List<? extends Number> list) {
       // Accepts List<Integer>, List<Double>, etc.
   }
   ```
   Conversely, contravariance uses the wildcard `super` to accept a broader type, allowing for more flexibility in method parameters:
   ```java
   public void addNumbers(List<? super Integer> list) {
       list.add(1); // Can add Integer or its subtypes
   }
   ```

5. **Type Erasure and Inheritance**: Java uses type erasure to implement generics, which means that generic type information is removed during compilation. This can affect inheritance because the runtime type information is not available, and you cannot instantiate a generic type directly:
   ```java
   // Cannot do: T obj = new T(); // Compile-time error due to type erasure
   ```
   This means that while generics provide compile-time safety, care must be taken when using inheritance with generics to avoid runtime issues.
