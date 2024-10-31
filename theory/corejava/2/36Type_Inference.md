
# Type Inference in Java

1. **Definition**: Type inference in Java is the ability of the compiler to automatically deduce the types of generic parameters based on the context in which they are used. This feature reduces the need for explicit type specifications, making code more concise and readable:
   ```java
   List<String> list = new ArrayList<>(); // Type inferred as ArrayList<String>
   ```

2. **Diamond Operator**: Introduced in Java 7, the diamond operator (`<>`) allows you to omit the type arguments on the right side when instantiating a generic class. The compiler infers the type from the variable declaration on the left:
   ```java
   Map<String, List<Integer>> map = new HashMap<>(); // Type inferred from the left side
   ```

3. **Generic Methods**: When calling generic methods, type inference enables the compiler to determine the type parameters based on the arguments passed to the method. This allows for cleaner method calls without needing to specify type arguments explicitly:
   ```java
   public static <T> void print(T item) {
       System.out.println(item);
   }
   print("Hello"); // Type inferred as String
   ```

4. **Bounded Type Parameters**: Type inference also works with bounded type parameters. When the compiler can deduce the type based on the method arguments and bounds specified, it provides a type-safe mechanism to utilize generics while maintaining flexibility:
   ```java
   public <T extends Number> void process(T number) {
       // T is inferred as Integer, Double, etc., based on the argument passed
   }
   ```

5. **Limitations**: While type inference simplifies the use of generics, there are scenarios where it cannot be performed, particularly when the type cannot be unambiguously determined. In such cases, explicit type parameters must be provided:
   ```java
   // Type inference can't determine the type in this case
   List<?> list = new ArrayList<>();
   // list.add("test"); // Compile-time error: cannot add elements
   ```
