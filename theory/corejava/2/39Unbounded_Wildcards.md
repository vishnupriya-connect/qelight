
# Unbounded Wildcards in Java

1. **Definition**: Unbounded wildcards are represented by a question mark (`?`) and allow you to use any type as an argument for generics. This means that you can pass any object type to methods that accept unbounded wildcards, making them very flexible:
   ```java
   public void printList(List<?> list) {
       for (Object item : list) {
           System.out.println(item);
       }
   }
   ```

2. **Use Cases**: Unbounded wildcards are useful when you don't need to know the specific type of the objects in the collection. They are commonly used in methods that operate on collections but do not require type-specific operations:
   ```java
   public void displayElements(Collection<?> collection) {
       for (Object element : collection) {
           System.out.println(element);
       }
   }
   ```

3. **Reading Items**: When using unbounded wildcards, you can read items from a collection as `Object` type. However, you cannot add any specific type of elements to the collection (except for `null`), as the type is not known:
   ```java
   List<?> list = new ArrayList<String>();
   // list.add("Hello"); // Compile-time error: cannot add to the list
   list.add(null); // Allowed
   ```

4. **Method Flexibility**: Methods that accept unbounded wildcards can accept arguments of any generic type, which makes them versatile in handling different types of collections. This is particularly useful in APIs where the specific type is irrelevant:
   ```java
   public void processItems(List<?> items) {
       // Can accept List<String>, List<Integer>, List<Double>, etc.
   }
   ```

5. **Type Safety Considerations**: While unbounded wildcards provide flexibility, they also reduce type safety because the compiler cannot guarantee the type of objects being handled. As a result, operations that rely on specific types cannot be performed without casting:
   ```java
   public void exampleMethod(List<?> list) {
       // String s = (String) list.get(0); // Unsafe cast, may lead to ClassCastException
   }
   ```
