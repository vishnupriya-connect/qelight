
# Declaring an Annotation Type in Java

1. **Syntax**: An annotation type is declared using the `@interface` keyword, similar to a class declaration. For example:
   ```java
   public @interface MyAnnotation {
   }
   ```

2. **Elements**: Annotations can have elements (methods) that act as attributes. Each element can have a default value. For example:
   ```java
   public @interface MyAnnotation {
       String value() default "default value";
       int count() default 0;
   }
   ```

3. **Retention Policy**: You can specify the retention policy using the `@Retention` annotation. It defines whether the annotation is available at source, class, or runtime:
   ```java
   import java.lang.annotation.Retention;
   import java.lang.annotation.RetentionPolicy;

   @Retention(RetentionPolicy.RUNTIME)
   public @interface MyAnnotation {
   }
   ```

4. **Targeting Annotations**: Use the `@Target` annotation to specify where the custom annotation can be applied (e.g., method, class, field):
   ```java
   import java.lang.annotation.ElementType;
   import java.lang.annotation.Target;

   @Target(ElementType.METHOD)
   public @interface MyAnnotation {
   }
   ```

5. **Documenting Annotations**: The `@Documented` annotation can be used to indicate that whenever the annotation is used, it should be included in the JavaDoc:
   ```java
   import java.lang.annotation.Documented;

   @Documented
   public @interface MyAnnotation {
   }
   ```
