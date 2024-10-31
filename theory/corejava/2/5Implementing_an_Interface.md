
# Implementing an Interface in Java

1. **Class Implementation**: A class implements an interface using the `implements` keyword. It must provide concrete implementations for all abstract methods declared in the interface. For example:
   ```java
   public class MyClass implements MyInterface {
       @Override
       public void myMethod() {
           System.out.println("Implementation of myMethod.");
       }
   }
   ```

2. **Multiple Interfaces**: A class can implement multiple interfaces, allowing for multiple inheritance of method signatures. This is done by listing the interfaces separated by commas:
   ```java
   public class MyClass implements Interface1, Interface2 {
       // Implement methods from both interfaces
   }
   ```

3. **Abstract Classes**: If a class implements an interface but does not provide implementations for all its methods, it must be declared as an abstract class. This allows the class to defer implementation to its subclasses:
   ```java
   public abstract class MyAbstractClass implements MyInterface {
       // Must implement myMethod in subclasses
   }
   ```

4. **Default Methods**: An interface can have default methods, which provide a default implementation. A class implementing the interface can choose to override these default methods if needed:
   ```java
   public class MyClass implements MyInterface {
       @Override
       public void myDefaultMethod() {
           System.out.println("Overridden default method.");
       }
   }
   ```

5. **Using Interface References**: You can use an interface type to reference an object of a class that implements that interface. This allows for polymorphic behavior, enabling you to write flexible and reusable code:
   ```java
   MyInterface obj = new MyClass();
   obj.myMethod(); // Calls MyClass's implementation
   ```
