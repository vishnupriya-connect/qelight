
# Defining an Interface in Java

1. **Syntax**: An interface in Java is defined using the `interface` keyword. It can contain abstract methods, default methods, and static methods. For example:
   ```java
   public interface MyInterface {
       void myMethod(); // Abstract method
       default void myDefaultMethod() {
           System.out.println("Default method implementation.");
       }
   }
   ```

2. **Abstract Methods**: All methods in an interface are implicitly public and abstract (unless they are default or static). Implementing classes must provide implementations for all abstract methods defined in the interface.

3. **Multiple Inheritance**: Interfaces allow a class to implement multiple interfaces, providing a way to achieve multiple inheritance in Java. For example:
   ```java
   public class MyClass implements MyInterface1, MyInterface2 {
       @Override
       public void myMethod() {
           // Implementation
       }
   }
   ```

4. **Constants**: Interfaces can contain constants, which are implicitly public, static, and final. These constants can be used by implementing classes. For example:
   ```java
   public interface MyConstants {
       int MY_CONSTANT = 100;
   }
   ```

5. **Marker Interfaces**: An interface with no methods or constants is called a marker interface. It is used to signal to the Java runtime that a class possesses a certain property or behavior. An example of a marker interface is `Serializable`.
