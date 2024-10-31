
# Writing Final Classes and Methods in Java

1. **Final Class**: A class declared with the `final` keyword cannot be subclassed or extended. This is useful when you want to prevent inheritance to maintain the integrity of the class, especially for utility classes or singleton patterns:
   ```java
   public final class UtilityClass {
       // Methods and fields
   }
   ```

2. **Final Method**: A method declared as `final` cannot be overridden by subclasses. This ensures that the method's behavior remains consistent and prevents any alteration by derived classes:
   ```java
   public class Parent {
       public final void display() {
           System.out.println("Display from Parent");
       }
   }

   public class Child extends Parent {
       // Cannot override display() method
   }
   ```

3. **Performance Benefits**: Using `final` for classes and methods can improve performance, as the Java compiler can optimize calls to `final` methods, knowing that they will not be overridden. This can lead to faster execution in certain scenarios.

4. **Best Practices**: It is recommended to use `final` for methods that are intended to be part of a stable API or when you want to enforce a specific implementation. Use it for classes that are not intended to be extended, such as helper classes or value objects.

5. **Immutable Classes**: Final classes are often used in the context of creating immutable objects. By making the class final and providing final fields (along with no setters), you can create objects whose state cannot be modified after creation, enhancing safety and predictability:
   ```java
   public final class ImmutablePoint {
       private final int x;
       private final int y;

       public ImmutablePoint(int x, int y) {
           this.x = x;
           this.y = y;
       }

       // Getters without setters
       public int getX() { return x; }
       public int getY() { return y; }
   }
   ```
