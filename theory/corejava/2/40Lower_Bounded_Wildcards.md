
# Lower Bounded Wildcards in Java

1. **Definition**: Lower bounded wildcards are defined using the syntax `<? super T>`, where T is the type you want to allow as an argument or its supertypes. This allows you to add instances of T or its subclasses to the collection, providing flexibility in adding elements:
   ```java
   public void addNumbers(List<? super Integer> list) {
       list.add(10); // Can add Integer and its subclasses
   }
   ```

2. **Use Cases**: Lower bounded wildcards are particularly useful when you need to ensure that a method can accept a broader type while still allowing for specific behavior on a derived type. They are commonly used in methods that perform write operations to collections:
   ```java
   List<Number> numberList = new ArrayList<>();
   addNumbers(numberList); // Accepts List<Number> or List<Object>
   ```

3. **Adding Elements**: When using lower bounded wildcards, you can safely add elements of type T or its subclasses to the collection. However, you cannot retrieve elements as a specific type since the type is not known beyond the specified lower bound:
   ```java
   public void addToList(List<? super Shape> shapes) {
       shapes.add(new Circle()); // Safe to add Circle, a subclass of Shape
   }
   ```

4. **Read-Only Restrictions**: While lower bounded wildcards allow adding elements, they restrict read operations. When retrieving elements from a collection defined with a lower bounded wildcard, you can only treat them as type `Object`:
   ```java
   public void processShapes(List<? super Circle> shapes) {
       Object shape = shapes.get(0); // Unsafe cast; only Object is guaranteed
   }
   ```

5. **Combining with Other Generics**: Lower bounded wildcards can be combined with other generic types to create more flexible and powerful methods. This allows for complex relationships between types while still maintaining type safety:
   ```java
   public <T> void copyElements(List<? super T> dest, List<T> src) {
       for (T item : src) {
           dest.add(item); // Safe to add item
       }
   }
   ```
