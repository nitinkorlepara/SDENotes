# Creational Design Patterns

- Provide object creation mechanisms that increase flexibility and reuse of existing code.
- Classification
  - Factory Method
  - Abstract Factory
  - Prototype
  - Singleton
  - Builder

### Singleton

- This ensures that a class has only one instance, while providing a global access point to this instance.

  ```
  //Single Threaded
  public final class Singleton {
      private static Singleton instance;
      public String value;

      private Singleton(String value) {
          // The following code emulates slow initialization.
          try {
              Thread.sleep(1000);
          } catch (InterruptedException ex) {
              ex.printStackTrace();
          }
          this.value = value;
      }

      public static Singleton getInstance(String value) {
          if (instance == null) {
              instance = new Singleton(value);
          }
          return instance;
      }
  }
  ```

### Prototype

- to create more instance of class that has to be created we could use prototype pattern
- ![Prototype](/SystemDesign/LLD/Images/Prototype.png)

### Simple Factory

- move the simple instantiation logic to a separate class and most commonly to a static method of this class.
- Example : java.text.NumberFormat has getInstance method
- ![NumberFormat](/SystemDesign/LLD/Images/NumberFormat.png)

### Factory Method

- provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.
- ![Factory Method](/SystemDesign/LLD/Images/FactoryMethod.png)

### Abstract Factory

- lets you produce families of related objects without specifying their concrete classes.

### References

1. [Creational Design Patterns](https://refactoring.guru/design-patterns/creational-patterns)
