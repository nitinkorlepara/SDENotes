# Creational Design Patterns

- Provide object creation mechanisms that increase flexibility and reuse of existing code.
- Classification
  - Factory Method
  - Abstract Factory
  - Prototype
  - Singleton
  - Builder

### Prototype

- to create more instance of class that has to be created we could use prototype pattern
- ![Prototype](/SystemDesign/DesignPatterns/Prototype.png)

### Simple Factory

- move the simple instantiation logic to a separate class and most commonly to a static method of this class.
- Example : java.text.NumberFormat has getInstance method
- ![NumberFormat](/SystemDesign/DesignPatterns/NumberFormat.png)

### Factory Method

- provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.
- ![Factory Method](/SystemDesign/DesignPatterns/FactoryMethod.png)

### Abstract Factory

- lets you produce families of related objects without specifying their concrete classes.

### References

1. [Creational Design Patterns](https://refactoring.guru/design-patterns/creational-patterns)
