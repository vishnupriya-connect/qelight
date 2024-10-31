
# Hiding Fields in Java

1. **Definition**: Hiding fields refers to the scenario where a subclass defines a field with the same name as a field in its superclass. The subclass field "hides" the superclass field, making it inaccessible via the subclass reference.

2. **Field Access**: When accessing fields, if a subclass and superclass both have a field with the same name, the reference type determines which field is accessed. This means that if you access the field through a superclass reference, the superclass field will be used:
   ```java
   class Parent {
       String name = "Parent Name";
   }

   class Child extends Parent {
       String name = "Child Name";
   }

   public class Test {
       public static void main(String[] args) {
           Parent p = new Child();
           System.out.println(p.name); // Outputs: "Parent Name"
       }
   }
   ```

3. **Use of `super` Keyword**: To access the hidden field from the superclass, you can use the `super` keyword within the subclass. This allows you to specify which field you want to refer to:
   ```java
   class Child extends Parent {
       String name = "Child Name";

       void printNames() {
           System.out.println(name);          // Outputs: "Child Name"
           System.out.println(super.name);    // Outputs: "Parent Name"
       }
   }
   ```

4. **No Overriding**: Unlike methods, fields are not overridden in Java. Hiding fields simply means that the subclass field takes precedence when accessed through a subclass reference, but the superclass field remains intact and accessible through a superclass reference.

5. **Best Practices**: It is generally advised to avoid hiding fields as it can lead to confusion and maintenance issues in code. Instead, use method overriding to achieve polymorphic behavior while maintaining clarity in your class design.
