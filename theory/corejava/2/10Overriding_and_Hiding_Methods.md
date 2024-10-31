
# Overriding and Hiding Methods in Java

1. **Method Overriding**: Method overriding occurs when a subclass provides a specific implementation for a method that is already defined in its superclass. The method in the subclass must have the same name, return type, and parameter list as in the superclass:
   ```java
   class Parent {
       void display() {
           System.out.println("Display from Parent");
       }
   }

   class Child extends Parent {
       @Override
       void display() {
           System.out.println("Display from Child");
       }
   }
   ```

2. **Access Modifiers**: When overriding a method, the access modifier in the subclass cannot be more restrictive than the one in the superclass. For example, if a method in the superclass is public, the overriding method in the subclass must also be public or protected, but not private.

3. **Static Methods and Hiding**: Method hiding occurs with static methods. If a subclass defines a static method with the same name and parameter list as a static method in the superclass, the method in the subclass hides the one in the superclass rather than overriding it:
   ```java
   class Parent {
       static void staticMethod() {
           System.out.println("Static method in Parent");
       }
   }

   class Child extends Parent {
       static void staticMethod() {
           System.out.println("Static method in Child");
       }
   }
   ```

4. **Calling Overridden Methods**: Within the subclass, you can call the overridden method from the superclass using the `super` keyword, allowing you to invoke the superclass's version of the method if needed:
   ```java
   class Child extends Parent {
       @Override
       void display() {
           super.display(); // Calls Parent's display method
           System.out.println("Display from Child");
       }
   }
   ```

5. **Dynamic Method Dispatch**: Java uses dynamic method dispatch to determine which method to invoke at runtime based on the object type. This enables polymorphism, allowing a subclass object to be treated as an instance of its superclass, with the correct method being called:
   ```java
   Parent obj = new Child(); // Upcasting
   obj.display(); // Calls Child's display method
   ```
