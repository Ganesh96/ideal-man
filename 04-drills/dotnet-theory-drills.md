# .NET Theory Drills

## Batch 1 — C# Foundation + OOP Foundation

### Definition Questions

1. What is the difference between a value type and a reference type?
2. What is the difference between a class and a struct?
3. What is encapsulation?
4. What is abstraction?
5. What is polymorphism?
6. What is inheritance?
7. What is the difference between a property and a field?
8. What is a nullable type?
9. What is an enum?
10. What is a constructor responsible for?

### Scenario Questions

1. A method receives an `Order` object and changes its status. Why might the caller observe that change?
2. A domain object has public setters for every property. What design problem can that create?
3. A team models `Order` as a struct. What risks does that create?
4. A status is represented as a string everywhere. What can go wrong?
5. A static mutable cache is used globally. What problems can appear in tests and production?

### Comparison Questions

1. Class vs struct.
2. Field vs property.
3. Inheritance vs composition.
4. Abstraction vs encapsulation.
5. Nullable value types vs nullable reference types.

### Failure-Mode Questions

1. What happens when mutable internal collections are exposed directly?
2. Why is saying value types always live on the stack misleading?
3. Why can deep inheritance hierarchies become fragile?
4. Why can static mutable state become dangerous?
5. Why should invalid states be difficult to represent?

### Interview Answer Questions

1. Explain value vs reference types in under 60 seconds.
2. Explain encapsulation using a business example.
3. Explain why composition is often preferred over inheritance.
4. Explain when an enum is useful and when it is limiting.
5. Explain nullable reference types and why they matter.
