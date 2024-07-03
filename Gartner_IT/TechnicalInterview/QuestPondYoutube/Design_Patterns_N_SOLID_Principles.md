### Interview Questions and Answers on Design Patterns and SOLID Principles

#### Design Patterns

**Q1: What are Design Patterns?**
- **Answer:** Design patterns are proven solutions to common problems in software design. They provide templates for solving issues that occur repeatedly in software development. They are categorized into creational, structural, and behavioral patterns.

**Q2: What are the different types of design patterns?**
- **Answer:** Design patterns are divided into three main categories:
  1. **Creational Patterns:** Focus on object creation mechanisms.
     - Examples: Singleton, Factory Method, Abstract Factory, Builder, Prototype.
  2. **Structural Patterns:** Deal with object composition.
     - Examples: Adapter, Composite, Decorator, Facade, Flyweight, Proxy.
  3. **Behavioral Patterns:** Concerned with object interaction.
     - Examples: Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, Observer, State, Strategy, Template Method, Visitor.

**Q3: Can you explain the Singleton Pattern and its use case?**
- **Answer:** The Singleton Pattern ensures a class has only one instance and provides a global point of access to it. It is useful for cases where exactly one object is needed to coordinate actions across the system, such as a configuration manager or logging class.

**Q4: How did you implement the Singleton Pattern in your project?**
- **Answer:**
  ```csharp
  public sealed class Singleton
  {
      private static readonly Lazy<Singleton> instance = new Lazy<Singleton>(() => new Singleton());
      public static Singleton Instance => instance.Value;
      private Singleton() { }
  }
  ```

**Q5: What is the Factory Pattern and when would you use it?**
- **Answer:** The Factory Pattern provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created. It's useful when the exact type of the object isn't known until runtime.
  ```csharp
  public interface IShape
  {
      void Draw();
  }
  
  public class Circle : IShape
  {
      public void Draw() { Console.WriteLine("Circle Drawn."); }
  }
  
  public class Square : IShape
  {
      public void Draw() { Console.WriteLine("Square Drawn."); }
  }
  
  public class ShapeFactory
  {
      public IShape GetShape(string shapeType)
      {
          if (shapeType == "CIRCLE") return new Circle();
          if (shapeType == "SQUARE") return new Square();
          return null;
      }
  }
  ```

**Q6: What is the difference between Adapter and Decorator Pattern?**
- **Answer:** 
  - **Adapter Pattern:** Converts the interface of a class into another interface the clients expect. It's used to make existing classes work with others without modifying their source code.
  - **Decorator Pattern:** Adds responsibilities to objects dynamically. It provides a flexible alternative to subclassing for extending functionality.

**Q7: Can you explain the Observer Pattern with an example?**
- **Answer:** The Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
  ```csharp
  public class Subject
  {
      private List<IObserver> observers = new List<IObserver>();
      
      public void Attach(IObserver observer)
      {
          observers.Add(observer);
      }
      
      public void Notify()
      {
          foreach (var observer in observers)
          {
              observer.Update();
          }
      }
  }
  
  public interface IObserver
  {
      void Update();
  }
  
  public class ConcreteObserver : IObserver
  {
      public void Update()
      {
          Console.WriteLine("Observer updated.");
      }
  }
  ```

#### SOLID Principles

**Q1: What are SOLID Principles?**
- **Answer:** SOLID is an acronym for five design principles aimed at making software designs more understandable, flexible, and maintainable:
  1. **Single Responsibility Principle (SRP)**
  2. **Open/Closed Principle (OCP)**
  3. **Liskov Substitution Principle (LSP)**
  4. **Interface Segregation Principle (ISP)**
  5. **Dependency Inversion Principle (DIP)**

**Q2: Can you explain the Single Responsibility Principle (SRP)?**
- **Answer:** SRP states that a class should have only one reason to change, meaning it should have only one job or responsibility. This principle helps in achieving a high cohesion and low coupling.
  ```csharp
  public class User
  {
      public void AddUser(string name)
      {
          // Add user to database
      }
  }
  
  public class Logger
  {
      public void Log(string message)
      {
          // Log message to a file or database
      }
  }
  ```

**Q3: What is the Open/Closed Principle (OCP)?**
- **Answer:** OCP states that software entities should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code.
  ```csharp
  public abstract class Shape
  {
      public abstract void Draw();
  }
  
  public class Circle : Shape
  {
      public override void Draw() { Console.WriteLine("Circle Drawn."); }
  }
  
  public class Square : Shape
  {
      public override void Draw() { Console.WriteLine("Square Drawn."); }
  }
  ```

**Q4: Explain the Liskov Substitution Principle (LSP) with an example.**
- **Answer:** LSP states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. This means that derived classes must be substitutable for their base classes.
  ```csharp
  public class Bird
  {
      public virtual void Fly() { }
  }
  
  public class Sparrow : Bird
  {
      public override void Fly() { }
  }
  
  public class Penguin : Bird
  {
      public override void Fly() 
      { 
          // Violates LSP as Penguins can't fly.
      }
  }
  ```

**Q5: What is the Interface Segregation Principle (ISP)?**
- **Answer:** ISP states that no client should be forced to depend on methods it does not use. This principle suggests creating smaller, more specific interfaces rather than large, monolithic ones.
  ```csharp
  public interface IPrinter
  {
      void Print();
  }
  
  public interface IScanner
  {
      void Scan();
  }
  
  public class MultiFunctionPrinter : IPrinter, IScanner
  {
      public void Print() { }
      public void Scan() { }
  }
  ```

**Q6: Can you explain the Dependency Inversion Principle (DIP)?**
- **Answer:** DIP states that high-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.
  ```csharp
  public interface IDatabase
  {
      void SaveData(string data);
  }
  
  public class SQLDatabase : IDatabase
  {
      public void SaveData(string data)
      {
          // Save data to SQL database
      }
  }
  
  public class DataManager
  {
      private readonly IDatabase _database;
  
      public DataManager(IDatabase database)
      {
          _database = database;
      }
  
      public void Save(string data)
      {
          _database.SaveData(data);
      }
  }
  ```

**Q7: How do you ensure your code adheres to SOLID principles?**
- **Answer:** Adhering to SOLID principles involves regular code reviews, writing unit tests, using design patterns appropriately, and refactoring code continuously. Applying these principles requires practice and awareness of their importance in maintaining a robust software design.

**Q8: Can you provide an example of a violation of the Single Responsibility Principle?**
- **Answer:** A class that handles multiple responsibilities violates SRP. For instance:
  ```csharp
  public class User
  {
      public void AddUser(string name)
      {
          // Add user to database
      }
  
      public void Log(string message)
      {
          // Log message to a file or database
      }
  }
  ```
  Here, the `User` class is handling both user management and logging, which should be separated.



### Deep Dive into Design Patterns and SOLID Principles

Let's delve deeper into design patterns and SOLID principles, understanding their concepts, use cases, and implementations.

---

## Design Patterns

### Creational Patterns

1. **Singleton Pattern**
   - **Purpose:** Ensures that a class has only one instance and provides a global point of access to it.
   - **Use Case:** Logging, configuration settings, thread pools.
   - **Implementation:**
     ```csharp
     public sealed class Singleton
     {
         private static readonly Lazy<Singleton> instance = new Lazy<Singleton>(() => new Singleton());
         public static Singleton Instance => instance.Value;
         private Singleton() { }
     }
     ```

2. **Factory Method Pattern**
   - **Purpose:** Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.
   - **Use Case:** When the exact type of object isn't known until runtime.
   - **Implementation:**
     ```csharp
     public interface IShape
     {
         void Draw();
     }

     public class Circle : IShape
     {
         public void Draw() { Console.WriteLine("Circle Drawn."); }
     }

     public class Square : IShape
     {
         public void Draw() { Console.WriteLine("Square Drawn."); }
     }

     public abstract class ShapeFactory
     {
         public abstract IShape CreateShape();
     }

     public class CircleFactory : ShapeFactory
     {
         public override IShape CreateShape() { return new Circle(); }
     }

     public class SquareFactory : ShapeFactory
     {
         public override IShape CreateShape() { return new Square(); }
     }
     ```

3. **Abstract Factory Pattern**
   - **Purpose:** Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
   - **Use Case:** When the system needs to be independent of how its objects are created, composed, and represented.
   - **Implementation:**
     ```csharp
     public interface IGUIFactory
     {
         IButton CreateButton();
         ICheckbox CreateCheckbox();
     }

     public class WinFactory : IGUIFactory
     {
         public IButton CreateButton() { return new WinButton(); }
         public ICheckbox CreateCheckbox() { return new WinCheckbox(); }
     }

     public class MacFactory : IGUIFactory
     {
         public IButton CreateButton() { return new MacButton(); }
         public ICheckbox CreateCheckbox() { return new MacCheckbox(); }
     }

     public class Application
     {
         private IButton button;
         private ICheckbox checkbox;

         public Application(IGUIFactory factory)
         {
             button = factory.CreateButton();
             checkbox = factory.CreateCheckbox();
         }

         public void CreateUI()
         {
             button.Paint();
             checkbox.Paint();
         }
     }
     ```

4. **Builder Pattern**
   - **Purpose:** Separates the construction of a complex object from its representation so that the same construction process can create different representations.
   - **Use Case:** When an object needs to be created with many possible configurations.
   - **Implementation:**
     ```csharp
     public class Product
     {
         public string PartA { get; set; }
         public string PartB { get; set; }
         public string PartC { get; set; }
     }

     public abstract class Builder
     {
         protected Product product = new Product();
         public abstract void BuildPartA();
         public abstract void BuildPartB();
         public abstract void BuildPartC();
         public Product GetResult() => product;
     }

     public class ConcreteBuilder : Builder
     {
         public override void BuildPartA() { product.PartA = "PartA"; }
         public override void BuildPartB() { product.PartB = "PartB"; }
         public override void BuildPartC() { product.PartC = "PartC"; }
     }

     public class Director
     {
         public void Construct(Builder builder)
         {
             builder.BuildPartA();
             builder.BuildPartB();
             builder.BuildPartC();
         }
     }
     ```

5. **Prototype Pattern**
   - **Purpose:** Specifies the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.
   - **Use Case:** When the cost of creating a new object is prohibitive.
   - **Implementation:**
     ```csharp
     public abstract class Prototype
     {
         public abstract Prototype Clone();
     }

     public class ConcretePrototype : Prototype
     {
         public int X { get; set; }
         public int Y { get; set; }

         public override Prototype Clone()
         {
             return (Prototype) this.MemberwiseClone();
         }
     }
     ```

### Structural Patterns

1. **Adapter Pattern**
   - **Purpose:** Converts the interface of a class into another interface the clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.
   - **Use Case:** Integrating new features or classes into an existing system without changing its existing code.
   - **Implementation:**
     ```csharp
     public interface ITarget
     {
         void Request();
     }

     public class Adaptee
     {
         public void SpecificRequest() { Console.WriteLine("Specific request."); }
     }

     public class Adapter : ITarget
     {
         private readonly Adaptee _adaptee;
         public Adapter(Adaptee adaptee) { _adaptee = adaptee; }
         public void Request() { _adaptee.SpecificRequest(); }
     }
     ```

2. **Decorator Pattern**
   - **Purpose:** Attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.
   - **Use Case:** Adding functionalities to objects without altering their structure.
   - **Implementation:**
     ```csharp
     public abstract class Component
     {
         public abstract void Operation();
     }

     public class ConcreteComponent : Component
     {
         public override void Operation() { Console.WriteLine("ConcreteComponent Operation."); }
     }

     public abstract class Decorator : Component
     {
         protected Component _component;
         public void SetComponent(Component component) { _component = component; }
         public override void Operation() { _component?.Operation(); }
     }

     public class ConcreteDecorator : Decorator
     {
         public override void Operation()
         {
             base.Operation();
             AddedBehavior();
         }

         void AddedBehavior() { Console.WriteLine("ConcreteDecorator AddedBehavior."); }
     }
     ```

3. **Facade Pattern**
   - **Purpose:** Provides a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.
   - **Use Case:** Simplifying a complex subsystem.
   - **Implementation:**
     ```csharp
     public class SubsystemA
     {
         public void OperationA() { Console.WriteLine("SubsystemA OperationA."); }
     }

     public class SubsystemB
     {
         public void OperationB() { Console.WriteLine("SubsystemB OperationB."); }
     }

     public class Facade
     {
         private readonly SubsystemA _subsystemA;
         private readonly SubsystemB _subsystemB;

         public Facade(SubsystemA subsystemA, SubsystemB subsystemB)
         {
             _subsystemA = subsystemA;
             _subsystemB = subsystemB;
         }

         public void Operation()
         {
             _subsystemA.OperationA();
             _subsystemB.OperationB();
         }
     }
     ```

### Behavioral Patterns

1. **Observer Pattern**
   - **Purpose:** Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
   - **Use Case:** Implementing event handling systems.
   - **Implementation:**
     ```csharp
     public interface IObserver
     {
         void Update();
     }

     public class ConcreteObserver : IObserver
     {
         public void Update() { Console.WriteLine("Observer updated."); }
     }

     public class Subject
     {
         private readonly List<IObserver> _observers = new List<IObserver>();

         public void Attach(IObserver observer) { _observers.Add(observer); }
         public void Detach(IObserver observer) { _observers.Remove(observer); }
         public void Notify()
         {
             foreach (var observer in _observers)
             {
                 observer.Update();
             }
         }
     }
     ```

2. **Strategy Pattern**
   - **Purpose:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
   - **Use Case:** Implementing different algorithms interchangeably.
   - **Implementation:**
     ```csharp
     public interface IStrategy
     {
         void Execute();
     }

     public class ConcreteStrategyA : IStrategy
     {
         public void Execute() { Console.WriteLine("ConcreteStrategyA Execution."); }
     }

     public class ConcreteStrategyB : IStrategy
     {
         public void Execute() { Console.WriteLine("ConcreteStrategyB Execution."); }
     }

     public class Context
     {
         private IStrategy _strategy;

         public void SetStrategy(IStrategy strategy) { _strategy = strategy; }
         public void ExecuteStrategy() { _strategy.Execute(); }
     }
     ```

3. **Command Pattern**
   - **Purpose:** Encapsulates a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.
   - **Use Case:** Implementing undo/redo functionalities.
   - **Implementation:**
     ```csharp
     public interface ICommand
     {
         void Execute();
     }

     public class Receiver
     {
         public void Action() {

 Console.WriteLine("Receiver Action."); }
     }

     public class ConcreteCommand : ICommand
     {
         private readonly Receiver _receiver;

         public ConcreteCommand(Receiver receiver) { _receiver = receiver; }
         public void Execute() { _receiver.Action(); }
     }

     public class Invoker
     {
         private ICommand _command;

         public void SetCommand(ICommand command) { _command = command; }
         public void ExecuteCommand() { _command.Execute(); }
     }
     ```

---

## SOLID Principles

### Single Responsibility Principle (SRP)

- **Purpose:** A class should have only one reason to change, meaning it should have only one job or responsibility.
- **Use Case:** Separating concerns in classes to ensure high cohesion and low coupling.
- **Example:**
  ```csharp
  public class User
  {
      public void AddUser(string name)
      {
          // Add user to database
      }
  }

  public class Logger
  {
      public void Log(string message)
      {
          // Log message to a file or database
      }
  }
  ```

### Open/Closed Principle (OCP)

- **Purpose:** Software entities should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code.
- **Use Case:** Enhancing software without altering existing, tested code.
- **Example:**
  ```csharp
  public abstract class Shape
  {
      public abstract void Draw();
  }

  public class Circle : Shape
  {
      public override void Draw() { Console.WriteLine("Circle Drawn."); }
  }

  public class Square : Shape
  {
      public override void Draw() { Console.WriteLine("Square Drawn."); }
  }
  ```

### Liskov Substitution Principle (LSP)

- **Purpose:** Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
- **Use Case:** Ensuring that derived classes extend the base classes without changing their behavior.
- **Example:**
  ```csharp
  public class Bird
  {
      public virtual void Fly() { }
  }

  public class Sparrow : Bird
  {
      public override void Fly() { }
  }

  public class Penguin : Bird
  {
      public override void Fly() 
      { 
          // Violates LSP as Penguins can't fly.
      }
  }
  ```

### Interface Segregation Principle (ISP)

- **Purpose:** No client should be forced to depend on methods it does not use. This principle suggests creating smaller, more specific interfaces rather than large, monolithic ones.
- **Use Case:** Creating interfaces that are client-specific to avoid implementing unnecessary methods.
- **Example:**
  ```csharp
  public interface IPrinter
  {
      void Print();
  }

  public interface IScanner
  {
      void Scan();
  }

  public class MultiFunctionPrinter : IPrinter, IScanner
  {
      public void Print() { }
      public void Scan() { }
  }
  ```

### Dependency Inversion Principle (DIP)

- **Purpose:** High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.
- **Use Case:** Decoupling software modules to increase maintainability and flexibility.
- **Example:**
  ```csharp
  public interface IDatabase
  {
      void SaveData(string data);
  }

  public class SQLDatabase : IDatabase
  {
      public void SaveData(string data)
      {
          // Save data to SQL database
      }
  }

  public class DataManager
  {
      private readonly IDatabase _database;

      public DataManager(IDatabase database)
      {
          _database = database;
      }

      public void Save(string data)
      {
          _database.SaveData(data);
      }
  }
  ```

By diving deep into each of these design patterns and SOLID principles, you'll gain a comprehensive understanding of how to implement them effectively in real-world scenarios and explain them confidently in interviews.