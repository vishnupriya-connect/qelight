
# Bounded Type Parameters in Java

1. **Definition**: Bounded type parameters allow you to restrict the types that can be used as type arguments in a generic class, interface, or method. This is done using the `extends` keyword to specify an upper bound (the class or interface that the type must extend):
   ```java
   public <T extends Number> void process(T number) {
       System.out.println("Processing: " + number);
   }
   ```

2. **Multiple Bounds**: You can specify multiple bounds for a type parameter by separating them with the `&` symbol. A type must satisfy all specified bounds, which can include both classes and interfaces:
   ```java
   public <T extends Number & Comparable<T>> void compare(T num1, T num2) {
       if (num1.compareTo(num2) > 0) {
           System.out.println(num1 + " is greater than " + num2);
       }
   }
   ```

3. **Use Cases**: Bounded type parameters are useful when you want to ensure that the types used with generics have specific properties or behaviors. For instance, if you need to perform arithmetic operations, you can restrict the type to `Number` or its subclasses:
   ```java
   public <T extends Number> double sum(T num1, T num2) {
       return num1.doubleValue() + num2.doubleValue();
   }
   ```

4. **Type Inference with Bounds**: When calling methods with bounded type parameters, Java can often infer the type arguments based on the arguments passed, allowing for concise method calls while maintaining type safety:
   ```java
   Integer a = 10;
   Integer b = 20;
   System.out.println(sum(a, b)); // Java infers T as Integer
   ```

5. **Combining Bounded Parameters with Wildcards**: You can use bounded type parameters in conjunction with wildcards for even more flexibility. This allows you to create methods that can accept a range of types while still maintaining some level of control over the types being used:
   ```java
   public void printNumbers(List<? extends Number> numbers) {
       for (Number num : numbers) {
           System.out.println(num);
       }
   }
   ```
