
# Abstract Methods and Classes in Java

1. **Definition**: An abstract class is a class that cannot be instantiated on its own and is meant to be subclassed. It can contain both abstract methods (without a body) and concrete methods (with a body). Abstract methods are declared using the `abstract` keyword:
   ```java
   abstract class Animal {
       abstract void makeSound(); // Abstract method
       void sleep() {             // Concrete method
           System.out.println("Sleeping...");
       }
   }
   ```

2. **Creating Subclasses**: Any class that extends an abstract class must provide implementations for all abstract methods, unless the subclass is also declared abstract. This enforces a contract for subclasses to implement specific behaviors:
   ```java
   class Dog extends Animal {
       @Override
       void makeSound() {
           System.out.println("Bark");
       }
   }
   ```

3. **Use Cases**: Abstract classes are used when there is a common base functionality among related classes, but some methods must be implemented differently by subclasses. They are useful for defining a template for future derived classes:
   ```java
   abstract class Shape {
       abstract double area(); // Abstract method
   }

   class Circle extends Shape {
       double radius;

       Circle(double radius) {
           this.radius = radius;
       }

       @Override
       double area() {
           return Math.PI * radius * radius; // Concrete implementation
       }
   }
   ```

4. **Cannot Instantiate Abstract Classes**: Attempting to create an instance of an abstract class directly will result in a compile-time error. You must create an instance of a concrete subclass that provides implementations for all abstract methods:
   ```java
   // Animal a = new Animal(); // Compile-time error
   Animal dog = new Dog(); // Correct usage
   ```

5. **Abstract Classes vs. Interfaces**: While both abstract classes and interfaces are used to achieve abstraction, abstract classes can have fields and constructors, and they can contain both abstract and concrete methods. In contrast, interfaces can only declare methods (prior to Java 8) and do not have any implementation, except for default methods introduced in Java 8.
