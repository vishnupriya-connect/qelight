
# Using Package Members in Java

1. **Accessing Classes in the Same Package**: When classes are defined within the same package, they can access each other's package-private and protected members without any import statements. This promotes encapsulation while allowing related classes to work together:
   ```java
   package com.example.myapp;

   class MyClass {
       void display() {
           System.out.println("Hello from MyClass!");
       }
   }

   public class Main {
       public static void main(String[] args) {
           MyClass myClass = new MyClass();
           myClass.display(); // Accessing package member
       }
   }
   ```

2. **Importing Classes from Other Packages**: To use classes from different packages, you must import them using the `import` statement. This allows you to reference classes without needing to use their fully qualified names:
   ```java
   import com.example.otherpackage.OtherClass; // Importing a class from another package

   public class Main {
       public static void main(String[] args) {
           OtherClass other = new OtherClass(); // Using the imported class
       }
   }
   ```

3. **Using Wildcards in Imports**: If you need to import multiple classes from the same package, you can use a wildcard (`*`) to simplify your import statements. However, this can reduce code readability and should be used judiciously:
   ```java
   import com.example.utilities.*; // Imports all classes from the utilities package
   ```

4. **Static Imports**: Java allows static members (fields and methods) of a class to be imported so that they can be accessed without needing to qualify them with the class name. This can make code cleaner, especially when using constants or utility methods:
   ```java
   import static java.lang.Math.*; // Importing all static members of Math class

   public class Main {
       public static void main(String[] args) {
           double result = sqrt(16); // Using static method without class name
           System.out.println(result);
       }
   }
   ```

5. **Access Modifiers and Package Scope**: Understanding access modifiers is crucial when using package members. Members with `public` access can be accessed from any other package, while `protected` members can be accessed by subclasses or classes in the same package. Default (package-private) members are only accessible within the same package:
   ```java
   package com.example.myapp;

   public class PublicClass {} // Accessible from anywhere
   class PackagePrivateClass {} // Accessible only within com.example.myapp
   protected class ProtectedClass {} // Accessible in subclasses and same package
   ```
