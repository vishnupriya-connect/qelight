
# Wildcards in Java

1. **Definition**: Wildcards in Java generics are special types denoted by the `?` symbol, allowing for flexibility in specifying the type of a generic parameter. They are particularly useful when you want to write methods that can accept various types of arguments without specifying exact types:
   ```java
   public void printList(List<?> list) {
       for (Object item : list) {
           System.out.println(item);
       }
   }
   ```

2. **Unbounded Wildcards**: An unbounded wildcard is represented by `?` and allows any type. It is useful when you don't need to know the specific type and want to work with multiple types interchangeably:
   ```java
   List<?> list = new ArrayList<String>(); // Can hold any type
   ```

3. **Upper Bounded Wildcards**: Upper bounded wildcards are specified using `<? extends T>`, where T is a type. This allows for accepting any type that is a subclass of T, enabling you to read items of that type while maintaining type safety:
   ```java
   public void processNumbers(List<? extends Number> numbers) {
       for (Number number : numbers) {
           System.out.println(number);
       }
   }
   ```

4. **Lower Bounded Wildcards**: Lower bounded wildcards are specified using `<? super T>`, where T is a type. This allows you to add items of type T or its subclasses to a collection, enabling more flexibility in writing to a collection:
   ```java
   public void addNumbers(List<? super Integer> list) {
       list.add(10); // Can add Integer or its subclasses
   }
   ```

5. **Use Cases**: Wildcards are commonly used in method parameters where the specific type is not essential, such as when writing utility methods or working with collections. They enhance code reusability and allow for more generic programming:
   ```java
   public void copyList(List<? extends T> source, List<? super T> dest) {
       for (T item : source) {
           dest.add(item); // Safe to add items
       }
   }
   ```
