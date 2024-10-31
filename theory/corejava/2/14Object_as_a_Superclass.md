
# Object as a Superclass in Java

1. **Root of the Class Hierarchy**: In Java, every class implicitly extends the `Object` class if no other superclass is specified. This means that all classes inherit methods and properties from `Object`, making it the ultimate superclass for all Java objects.

2. **Common Methods**: The `Object` class provides several fundamental methods that can be overridden by subclasses, including:
   - `toString()`: Returns a string representation of the object.
   - `equals(Object obj)`: Compares two objects for equality.
   - `hashCode()`: Returns a hash code value for the object, which is useful in hashing data structures.
   ```java
   @Override
   public String toString() {
       return "MyClass instance";
   }
   ```

3. **Polymorphism**: Because all classes inherit from `Object`, you can refer to any object using an `Object` reference. This enables polymorphic behavior, allowing methods to accept objects of any class and perform operations based on the actual object type:
   ```java
   void printObject(Object obj) {
       System.out.println(obj.toString());
   }
   ```

4. **Type Casting**: When working with objects as instances of `Object`, you may need to cast them back to their original type to access specific methods or properties. This can be done using explicit casting, but it requires careful handling to avoid `ClassCastException`:
   ```java
   Object obj = new String("Hello");
   String str = (String) obj; // Casting back to String
   ```

5. **Use in Collections**: The `Object` type is often used in Java Collections (like `ArrayList`), allowing for the storage of any type of object. However, when retrieving objects from a collection, you'll often need to cast them to their specific type:
   ```java
   List<Object> myList = new ArrayList<>();
   myList.add("Hello");
   String greeting = (String) myList.get(0); // Cast to String
   ```
