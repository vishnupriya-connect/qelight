
# Using the Keyword `super` in Java

1. **Accessing Superclass Methods**: The `super` keyword is used to call methods from the superclass that have been overridden in the subclass. This allows the subclass to utilize the functionality of the superclass method while adding or modifying behavior:
   ```java
   class Parent {
       void display() {
           System.out.println("Display from Parent");
       }
   }

   class Child extends Parent {
       void display() {
           super.display(); // Calls Parent's display method
           System.out.println("Display from Child");
       }
   }
   ```

2. **Accessing Superclass Fields**: You can use `super` to access hidden fields in the superclass. If a subclass has a field with the same name as a superclass field, `super` can be used to refer specifically to the superclass field:
   ```java
   class Parent {
       String name = "Parent";
   }

   class Child extends Parent {
       String name = "Child";

       void printNames() {
           System.out.println(name);         // Outputs: "Child"
           System.out.println(super.name);   // Outputs: "Parent"
       }
   }
   ```

3. **Calling Superclass Constructor**: The `super` keyword can also be used to call a superclass constructor. This is especially useful when the superclass has a parameterized constructor, allowing the subclass to initialize the inherited part of the object:
   ```java
   class Parent {
       Parent(String name) {
           System.out.println("Parent constructor: " + name);
       }
   }

   class Child extends Parent {
       Child(String name) {
           super(name); // Calls Parent constructor
           System.out.println("Child constructor");
       }
   }
   ```

4. **First Statement in Constructor**: When using `super` to call a superclass constructor, it must be the first statement in the subclass constructor. If omitted, the Java compiler will automatically insert a call to the no-argument constructor of the superclass:
   ```java
   class Child extends Parent {
       Child() {
           super("Default Name"); // Must be first
       }
   }
   ```

5. **Clarifying Ambiguity**: The `super` keyword helps clarify ambiguity in cases where both the superclass and subclass contain methods or fields with the same name. By explicitly using `super`, the developer can specify which method or field is intended to be used, improving code readability and maintainability.
