
# Default Methods in Java

1. **Definition**: Default methods are methods in interfaces that have a body. Introduced in Java 8, they allow developers to add new methods to interfaces without breaking existing implementations.
   ```java
   public interface MyInterface {
       default void myDefaultMethod() {
           System.out.println("This is a default method.");
       }
   }
   ```

2. **Implementation in Classes**: Classes that implement an interface with default methods can either use the default implementation or provide their own override. If a class does not override a default method, the default implementation is used:
   ```java
   public class MyClass implements MyInterface {
       @Override
       public void myDefaultMethod() {
           System.out.println("Overridden default method.");
       }
   }
   ```

3. **Multiple Inheritance of Default Methods**: If a class implements multiple interfaces that contain the same default method, it must provide an explicit implementation to resolve the ambiguity:
   ```java
   public interface InterfaceA {
       default void commonMethod() {
           System.out.println("Interface A default method.");
       }
   }

   public interface InterfaceB {
       default void commonMethod() {
           System.out.println("Interface B default method.");
       }
   }

   public class MyClass implements InterfaceA, InterfaceB {
       @Override
       public void commonMethod() {
           System.out.println("MyClass implementation.");
       }
   }
   ```

4. **Benefits**: Default methods facilitate the evolution of interfaces by allowing developers to introduce new methods without breaking existing code. This enhances flexibility and maintainability in large codebases.

5. **Use Cases**: Default methods are useful for providing common functionality that can be reused across multiple classes, allowing for cleaner code and reducing redundancy. They are often used in frameworks to add new features while maintaining compatibility with older versions.
