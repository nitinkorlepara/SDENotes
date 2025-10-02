# MicroServices

### AOP (Aspect Oriented Programming)

- AOP decouples the cross cutting concerns from the actual business logic
- Aspect ( java class ) Which contains logic that handles cross cutting concerns
- Advice : Action
  - Before advice: Advice that executes before a joinpoint
  - After returning advice: Advice to be executed after a joinpoint completes normally, for example, a method returns without throwing an exception
  - After throwing advice: Advice to be executed if a method exits by throwing an exception
  - After (finally) advice: Advice to be executed regardless of the means by which a join point exits
  - Around advice: Advice that surrounds a join point such as method invocation. This is the most powerful kind of advice
- Joint point : Any point of the execution in the program
- Point Cut - Expression languge which AOP understands
- Target - one object which is being advice
- Proxy - Implment Aspects
  **Cross Cutting Concerns**

- A Concern is a term that refers to a part of the system divided on the basis of the functionality.
- Types
  - Core Concerns - Primary Functionality (business logic)
  - System-wide Concerns( logging, security)
    ![CCS](/Frameworks/CrossCuttingConcerns.png)

### References

-
