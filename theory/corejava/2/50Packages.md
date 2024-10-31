
# Packages in Java

1. **Definition**: A package in Java is a namespace that organizes a set of related classes and interfaces. It helps avoid naming conflicts and can control access with its protected and default access levels. Packages make it easier to manage large software projects by grouping related functionalities:
   ```java
   package com.example.myapp; // Declaring a package
   ```

2. **Built-in Packages**: Java provides a rich set of built-in packages that contain reusable classes and interfaces. Some common packages include:
   - `java.lang`: Contains fundamental classes such as `String`, `Math`, and `System` (automatically imported).
   - `java.util`: Contains utility classes like `ArrayList`, `HashMap`, and `Date`.
   - `java.io`: Contains classes for input and output through data streams, serialization, and file handling.

3. **Creating Custom Packages**: To create a custom package, declare the package at the top of your Java source file using the `package` keyword. The directory structure should match the package name to avoid issues during compilation:
   ```java
   package com.mycompany.myapp; // Custom package declaration
   ```
   Make sure the corresponding directory structure exists (e.g., `com/mycompany/myapp`).
   
4. **Access Modifiers and Package Protection**: Java uses access modifiers (public, protected, private, and default) to control visibility within packages. Classes and members with no modifier (default access) are accessible only within the same package, while `public` members are accessible from any other package:
   ```java
   public class PublicClass {} // Accessible from any package
   class DefaultClass {} // Accessible only within the same package
   ```

5. **Importing Packages**: To use classes from other packages, you need to import them into your Java file using the `import` statement. You can import specific classes or entire packages. For example:
   ```java
   import java.util.List; // Importing a specific class
   import java.util.*; // Importing all classes from the java.util package
   ```
