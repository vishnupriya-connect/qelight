
# Polymorphism in Java

1. **Definition**: Polymorphism is the ability of an object to take on many forms. In Java, it allows methods to perform different tasks based on the object that invokes them, enhancing flexibility and reusability in code.

2. **Types of Polymorphism**: There are two main types of polymorphism in Java:
   - **Compile-time Polymorphism** (Method Overloading): Achieved by defining multiple methods with the same name but different parameter lists within the same class or in subclasses.
   - **Runtime Polymorphism** (Method Overriding): Occurs when a subclass provides a specific implementation of a method already defined in its superclass.

3. **Method Overloading Example**: Method overloading enables different implementations based on the parameter types or counts. For example:
   ```java
   class MathUtil {
       int add(int a, int b) {
           return a + b;
       }

       double add(double a, double b) {
           return a + b;
       }
   }
   ```

4. **Method Overriding Example**: Runtime polymorphism is achieved through method overriding, where a subclass provides a specific implementation of a method defined in its superclass. For example:
   ```java
   class Animal {
       void sound() {
           System.out.println("Animal makes sound");
       }
   }

   class Dog extends Animal {
       @Override
       void sound() {
           System.out.println("Dog barks");
       }
   }
   ```

5. **Dynamic Method Dispatch**: Java implements polymorphism using dynamic method dispatch, where the method to be executed is determined at runtime based on the actual object type. This allows for more flexible and maintainable code:
   ```java
   Animal myAnimal = new Dog(); // Upcasting
   myAnimal.sound(); // Calls Dog's sound method
   ```
