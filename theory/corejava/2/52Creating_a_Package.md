
# Creating a Package in Java

1. **Package Declaration**: To create a package, start your Java source file with the `package` keyword followed by the package name. The package declaration must be the first statement in the file (excluding comments):
   ```java
   package com.example.myapp; // Declaring a package
   ```

2. **Directory Structure**: The directory structure on your file system must match the package name. For example, if your package is `com.example.myapp`, create a folder structure like `com/example/myapp` and place your Java file in the `myapp` directory:
   ```plaintext
   src/
       com/
           example/
               myapp/
                   MyClass.java
   ```

3. **Compiling the Package**: When you compile a Java file that is part of a package, navigate to the parent directory of the package structure and use the `javac` command. For example:
   ```bash
   javac com/example/myapp/MyClass.java
   ```
   This will create the corresponding `.class` files in the same directory structure.

4. **Access Modifiers**: Classes defined in a package can have different access modifiers (`public`, `protected`, `private`, and default). The default access modifier restricts visibility to classes within the same package, while `public` allows access from other packages:
   ```java
   public class PublicClass {} // Can be accessed from any package
   class DefaultClass {} // Accessible only within com.example.myapp package
   ```

5. **Best Practices for Naming Packages**: It is a common convention to use reverse domain names for package naming to avoid naming conflicts. For example, if your company domain is `example.com`, use package names like `com.example.project`:
   ```java
   package com.example.utils; // Package for utility classes
   ```
