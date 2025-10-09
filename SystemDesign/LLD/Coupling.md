## What is Coupling?

**Coupling** refers to the degree of interdependence between software modules or classes. It measures how closely connected two classes or modules are and how much one class knows about the inner workings of another.

## Tight Coupling vs Loose Coupling

### **Tight Coupling**

- Classes are highly dependent on each other
- Changes in one class require changes in dependent classes
- Difficult to test, maintain, and reuse
- Hard to replace implementations

```
class PetrolEngine {
    public void start() {
        System.out.println("Petrol engine starting... Vroom!");
    }
}
class Car {
    // PROBLEM: Car directly creates and depends on PetrolEngine
    private PetrolEngine engine = new PetrolEngine();
    public void drive() {
        engine.start();
        System.out.println("Car is driving...");
    }
}
```

### **Loose Coupling**

- Classes have minimal dependencies
- Changes in one class have minimal impact on others
- Easy to test, maintain, and reuse
- Easy to replace implementations

```
interface Engine {
    void start();
}
class PetrolEngine2 implements Engine {
    public void start() {
        System.out.println("Petrol engine starting... Vroom!");
    }
}
class ElectricEngine implements Engine {
    public void start() {
        System.out.println("Electric engine starting... Whirr!");
    }

// Car is LOOSELY COUPLED - depends on interface
class FlexibleCar {
    // SOLUTION: Depend on interface, not concrete class
    private Engine engine;
    // Inject dependency through constructor
    public FlexibleCar(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is driving...");
    }
}

```

## Benefits of Loose Coupling

1. **Maintainability**: Easier to modify and update code
2. **Testability**: Easier to write unit tests
3. **Reusability**: Components can be reused in different contexts
4. **Flexibility**: Easy to swap implementations
5. **Scalability**: Easier to extend functionality
