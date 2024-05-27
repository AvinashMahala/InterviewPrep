### Object-Oriented Programming (OOP) Interview Questions:

1. **What are the fundamental principles of object-oriented programming (OOP)?**
   - Answer: The four fundamental principles are Encapsulation, Abstraction, Inheritance, and Polymorphism.

2. **What is encapsulation and how is it implemented in OOP?**
   - Answer: Encapsulation is the bundling of data and methods that operate on that data within a single unit, or class, and restricting access to some of the object's components. It is implemented using access modifiers like private, protected, and public.

3. **Explain the concept of abstraction in OOP.**
   - Answer: Abstraction is the process of hiding the complex implementation details and showing only the essential features of the object. It is achieved using abstract classes and interfaces.

4. **What is inheritance in OOP and why is it useful?**
   - Answer: Inheritance is a mechanism where one class (derived class) inherits the properties and behavior of another class (base class). It promotes code reuse and establishes a natural hierarchy between classes.

5. **Define polymorphism and provide an example.**
   - Answer: Polymorphism allows methods to do different things based on the object it is acting upon, typically achieved through method overriding (runtime polymorphism) and method overloading (compile-time polymorphism).
     - Example: 
       ```csharp
       public class Animal
       {
           public virtual void Speak() { Console.WriteLine("Animal sound"); }
       }
       
       public class Dog : Animal
       {
           public override void Speak() { Console.WriteLine("Bark"); }
       }
       
       Animal myDog = new Dog();
       myDog.Speak(); // Output: Bark
       ```

6. **What is the difference between an abstract class and an interface?**
   - Answer: An abstract class can have both abstract and non-abstract methods and can contain fields, properties, and constructors. An interface can only have method signatures (without implementations) and properties without access modifiers.

7. **What is a constructor in OOP and what is its purpose?**
   - Answer: A constructor is a special method in a class that is called when an object of the class is instantiated. It is used to initialize the object's properties.

8. **Explain method overloading and method overriding.**
   - Answer: Method overloading allows multiple methods in the same class to have the same name but different parameters. Method overriding allows a derived class to provide a specific implementation of a method already defined in its base class.

9. **What is an object in OOP?**
   - Answer: An object is an instance of a class. It contains fields (data) and methods (functions) that define its behavior.

10. **What is a class in OOP?**
    - Answer: A class is a blueprint for creating objects. It defines properties and methods that the created objects will have.

11. **Explain the concept of an interface in OOP.**
    - Answer: An interface is a contract that defines a set of methods and properties that a class must implement. Interfaces provide a way to achieve abstraction and multiple inheritance.

12. **What is the difference between private, protected, and public access modifiers?**
    - Answer: 
      - `private`: The member is accessible only within the same class.
      - `protected`: The member is accessible within the same class and by derived classes.
      - `public`: The member is accessible from any other class.

13. **What is a destructor in OOP and what is its purpose?**
    - Answer: A destructor is a method that is called when an object is destroyed. It is used to clean up resources allocated by the object. In C#, it is defined using a tilde (~) followed by the class name.

14. **What is the difference between composition and inheritance?**
    - Answer: Composition is a "has-a" relationship where a class contains an object of another class as a member, promoting reuse without extending functionality. Inheritance is an "is-a" relationship where a class derives from another class, inheriting its properties and behavior.

15. **Explain the concept of a static class in OOP.**
    - Answer: A static class cannot be instantiated and can contain only static members. It is used to create utility classes that provide functionality without needing an object.

16. **What is an abstract method?**
    - Answer: An abstract method is a method without an implementation that must be overridden in derived classes. It is declared within an abstract class.

17. **How does polymorphism benefit OOP?**
    - Answer: Polymorphism allows for flexibility and the ability to define methods that can behave differently based on the object that calls them. This makes code more maintainable and scalable.

18. **What is a property in OOP and how is it used?**
    - Answer: A property is a member of a class that provides a flexible mechanism to read, write, or compute the values of private fields. Properties are used to encapsulate data within a class.

19. **Explain the role of the `this` keyword in OOP.**
    - Answer: The `this` keyword refers to the current instance of the class. It is used to access members of the current object, especially when there is a name conflict between class members and parameters.

20. **What is the difference between a deep copy and a shallow copy?**
    - Answer: A shallow copy copies the object's values (including references to other objects), whereas a deep copy copies the object and all objects it references, creating completely independent copies.
