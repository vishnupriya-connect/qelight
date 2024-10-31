
# Generic Types in Java

1. **Definition**: Generic types are classes or interfaces that can operate on types specified as parameters. This allows for the creation of reusable data structures and algorithms that work with any object type while maintaining type safety:
   ```java
   public class Box<T> {
       private T item;

       public void setItem(T item) {
           this.item = item;
       }

       public T getItem() {
           return item;
       }
   }
   ```

2. **Type Parameters**: When defining a generic type, you can specify one or more type parameters within angle brackets. Common conventions include using single uppercase letters, such as `T`, `E` (element), `K` (key), and `V` (value):
   ```java
   public class Pair<K, V> {
       private K key;
       private V value;

       public Pair(K key, V value) {
           this.key = key;
           this.value = value;
       }
   }
   ```

3. **Type Inference**: Java provides type inference, which allows the compiler to automatically determine the type arguments based on the context in which a generic type is used. This simplifies code writing and improves readability:
   ```java
   Box<String> stringBox = new Box<>(); // Type inference for the constructor
   ```

4. **Bounded Type Parameters**: You can restrict the types that can be used as type arguments by using bounded type parameters. This is done with the `extends` keyword to specify an upper bound or `super` for a lower bound:
   ```java
   public <T extends Number> void processNumber(T number) {
       // Method can accept any subclass of Number (e.g., Integer, Double)
   }
   ```

5. **Generic Methods**: In addition to generic classes, you can define methods that have their own type parameters. This allows methods to be more flexible and to work with different types without being tied to a specific class type:
   ```java
   public static <T> void printArray(T[] array) {
       for (T element : array) {
           System.out.println(element);
       }
   }
   ```
