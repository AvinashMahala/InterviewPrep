### Design Patterns Interview Questions and Answers

---

#### Creational Design Patterns

**1. What are creational design patterns?**
**Answer:** Creational design patterns deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. They abstract the instantiation process and help make a system independent of how its objects are created, composed, and represented.

---

**2. Can you explain the Singleton pattern and provide an example?**
**Answer:** The Singleton pattern ensures that a class has only one instance and provides a global point of access to it. This is useful when exactly one object is needed to coordinate actions across the system.

**Example:**
```csharp
public class Singleton
{
    private static Singleton _instance;
    private static readonly object _lock = new object();

    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            lock (_lock)
            {
                if (_instance == null)
                {
                    _instance = new Singleton();
                }
                return _instance;
            }
        }
    }

    public void DoSomething()
    {
        Console.WriteLine("Singleton instance is doing something.");
    }
}
```

---

**3. What is the Factory Method pattern?**
**Answer:** The Factory Method pattern defines an interface for creating an object but lets subclasses alter the type of objects that will be created. It promotes loose coupling by eliminating the need to bind application-specific classes into the code.

**Example:**
```csharp
public abstract class Product
{
    public abstract void Operation();
}

public class ConcreteProductA : Product
{
    public override void Operation()
    {
        Console.WriteLine("Operation of ConcreteProductA.");
    }
}

public class ConcreteProductB : Product
{
    public override void Operation()
    {
        Console.WriteLine("Operation of ConcreteProductB.");
    }
}

public abstract class Creator
{
    public abstract Product FactoryMethod();

    public void AnOperation()
    {
        var product = FactoryMethod();
        product.Operation();
    }
}

public class ConcreteCreatorA : Creator
{
    public override Product FactoryMethod()
    {
        return new ConcreteProductA();
    }
}

public class ConcreteCreatorB : Creator
{
    public override Product FactoryMethod()
    {
        return new ConcreteProductB();
    }
}
```

---

**4. What is the Abstract Factory pattern?**
**Answer:** The Abstract Factory pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes. It allows clients to create objects without knowing their specific types, promoting consistency among products.

**Example:**
```csharp
public interface IAbstractFactory
{
    IProductA CreateProductA();
    IProductB CreateProductB();
}

public interface IProductA
{
    void OperationA();
}

public interface IProductB
{
    void OperationB();
}

public class ConcreteFactory1 : IAbstractFactory
{
    public IProductA CreateProductA()
    {
        return new ConcreteProductA1();
    }

    public IProductB CreateProductB()
    {
        return new ConcreteProductB1();
    }
}

public class ConcreteFactory2 : IAbstractFactory
{
    public IProductA CreateProductA()
    {
        return new ConcreteProductA2();
    }

    public IProductB CreateProductB()
    {
        return new ConcreteProductB2();
    }
}

public class ConcreteProductA1 : IProductA
{
    public void OperationA()
    {
        Console.WriteLine("Operation of ConcreteProductA1.");
    }
}

public class ConcreteProductA2 : IProductA
{
    public void OperationA()
    {
        Console.WriteLine("Operation of ConcreteProductA2.");
    }
}

public class ConcreteProductB1 : IProductB
{
    public void OperationB()
    {
        Console.WriteLine("Operation of ConcreteProductB1.");
    }
}

public class ConcreteProductB2 : IProductB
{
    public void OperationB()
    {
        Console.WriteLine("Operation of ConcreteProductB2.");
    }
}
```

---

**5. What is the Builder pattern?**
**Answer:** The Builder pattern separates the construction of a complex object from its representation so that the same construction process can create different representations. It is useful for creating objects that require multiple steps to construct.

**Example:**
```csharp
public class Product
{
    public string PartA { get; set; }
    public string PartB { get; set; }
    public string PartC { get; set; }
}

public interface IBuilder
{
    void BuildPartA();
    void BuildPartB();
    void BuildPartC();
    Product GetResult();
}

public class ConcreteBuilder : IBuilder
{
    private Product _product = new Product();

    public void BuildPartA()
    {
        _product.PartA = "PartA";
    }

    public void BuildPartB()
    {
        _product.PartB = "PartB";
    }

    public void BuildPartC()
    {
        _product.PartC = "PartC";
    }

    public Product GetResult()
    {
        return _product;
    }
}

public class Director
{
    private IBuilder _builder;

    public Director(IBuilder builder)
    {
        _builder = builder;
    }

    public void Construct()
    {
        _builder.BuildPartA();
        _builder.BuildPartB();
        _builder.BuildPartC();
    }
}

// Usage
var builder = new ConcreteBuilder();
var director = new Director(builder);
director.Construct();
Product product = builder.GetResult();
```

---

#### Structural Design Patterns

**6. What are structural design patterns?**
**Answer:** Structural design patterns deal with object composition, forming larger structures from individual objects and classes. They simplify the design by identifying a simple way to realize relationships between entities.

---

**7. Can you explain the Adapter pattern and provide an example?**
**Answer:** The Adapter pattern allows incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces, converting the interface of a class into another interface that the client expects.

**Example:**
```csharp
public interface ITarget
{
    void Request();
}

public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Specific request.");
    }
}

public class Adapter : ITarget
{
    private Adaptee _adaptee;

    public Adapter(Adaptee adaptee)
    {
        _adaptee = adaptee;
    }

    public void Request()
    {
        _adaptee.SpecificRequest();
    }
}

// Usage
ITarget target = new Adapter(new Adaptee());
target.Request();
```

---

**8. What is the Bridge pattern?**
**Answer:** The Bridge pattern decouples an abstraction from its implementation so that the two can vary independently. It is used to separate the abstraction (interface) from its implementation (concrete classes).

**Example:**
```csharp
public abstract class Implementor
{
    public abstract void OperationImpl();
}

public class ConcreteImplementorA : Implementor
{
    public override void OperationImpl()
    {
        Console.WriteLine("ConcreteImplementorA Operation");
    }
}

public class ConcreteImplementorB : Implementor
{
    public override void OperationImpl()
    {
        Console.WriteLine("ConcreteImplementorB Operation");
    }
}

public abstract class Abstraction
{
    protected Implementor implementor;

    protected Abstraction(Implementor implementor)
    {
        this.implementor = implementor;
    }

    public abstract void Operation();
}

public class RefinedAbstraction : Abstraction
{
    public RefinedAbstraction(Implementor implementor) : base(implementor) { }

    public override void Operation()
    {
        implementor.OperationImpl();
    }
}

// Usage
Abstraction abstraction = new RefinedAbstraction(new ConcreteImplementorA());
abstraction.Operation();
```

---

**9. What is the Composite pattern?**
**Answer:** The Composite pattern allows you to compose objects into tree structures to represent part-whole hierarchies. It lets clients treat individual objects and compositions of objects uniformly.

**Example:**
```csharp
public abstract class Component
{
    public abstract void Operation();
}

public class Leaf : Component
{
    public override void Operation()
    {
        Console.WriteLine("Leaf operation");
    }
}

public class Composite : Component
{
    private List<Component> _children = new List<Component>();

    public void Add(Component component)
    {
        _children.Add(component);
    }

    public void Remove(Component component)
    {
        _children.Remove(component);
    }

    public override void Operation()
    {
        foreach (var child in _children)
        {
            child.Operation();
        }
    }
}

// Usage
Composite root = new Composite();
root.Add(new Leaf());
Composite subtree = new Composite();
subtree.Add(new Leaf());
root.Add(subtree);
root.Operation();
```

---

**10. What is the Decorator pattern?**
**Answer:** The Decorator pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.

**Example:**
```csharp
public abstract class Component
{
    public abstract void Operation();
}

public class ConcreteComponent : Component
{
    public override void Operation()
    {
        Console.WriteLine("ConcreteComponent operation");
    }
}

public abstract class Decorator : Component
{
    protected Component _component;

    public void SetComponent(Component component)
    {
        _component = component;
    }

    public override void Operation()
    {
        _component?.Operation();
    }
}

public class ConcreteDecoratorA : Decorator
{
    public override void Operation()
    {
        base.Operation();
        Console.WriteLine("ConcreteDecoratorA operation");
    }
}

public class ConcreteDecoratorB : Decorator
{
    public override void Operation()
    {
        base.Operation();
        Console.WriteLine("ConcreteDecoratorB operation");


    }
}

// Usage
ConcreteComponent component = new ConcreteComponent();
ConcreteDecoratorA decoratorA = new ConcreteDecoratorA();
ConcreteDecoratorB decoratorB = new ConcreteDecoratorB();

decoratorA.SetComponent(component);
decoratorB.SetComponent(decoratorA);
decoratorB.Operation();
```

---

**11. What is the Facade pattern?**
**Answer:** The Facade pattern provides a simplified interface to a complex subsystem. It defines a higher-level interface that makes the subsystem easier to use.

**Example:**
```csharp
public class SubsystemA
{
    public void OperationA()
    {
        Console.WriteLine("SubsystemA operation");
    }
}

public class SubsystemB
{
    public void OperationB()
    {
        Console.WriteLine("SubsystemB operation");
    }
}

public class Facade
{
    private SubsystemA _subsystemA;
    private SubsystemB _subsystemB;

    public Facade()
    {
        _subsystemA = new SubsystemA();
        _subsystemB = new SubsystemB();
    }

    public void Operation()
    {
        _subsystemA.OperationA();
        _subsystemB.OperationB();
    }
}

// Usage
Facade facade = new Facade();
facade.Operation();
```

---

#### Behavioral Design Patterns

**12. What are behavioral design patterns?**
**Answer:** Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects. They help in communication between objects and how objects interact with each other.

---

**13. Can you explain the Observer pattern and provide an example?**
**Answer:** The Observer pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically. It is commonly used in implementing distributed event handling systems.

**Example:**
```csharp
public interface IObserver
{
    void Update(string message);
}

public class ConcreteObserver : IObserver
{
    private string _name;

    public ConcreteObserver(string name)
    {
        _name = name;
    }

    public void Update(string message)
    {
        Console.WriteLine($"{_name} received update: {message}");
    }
}

public interface ISubject
{
    void Attach(IObserver observer);
    void Detach(IObserver observer);
    void Notify(string message);
}

public class ConcreteSubject : ISubject
{
    private List<IObserver> _observers = new List<IObserver>();

    public void Attach(IObserver observer)
    {
        _observers.Add(observer);
    }

    public void Detach(IObserver observer)
    {
        _observers.Remove(observer);
    }

    public void Notify(string message)
    {
        foreach (var observer in _observers)
        {
            observer.Update(message);
        }
    }
}

// Usage
ConcreteSubject subject = new ConcreteSubject();
subject.Attach(new ConcreteObserver("Observer1"));
subject.Attach(new ConcreteObserver("Observer2"));

subject.Notify("State has changed.");
```

---

**14. What is the Strategy pattern?**
**Answer:** The Strategy pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. The strategy pattern lets the algorithm vary independently from clients that use it.

**Example:**
```csharp
public interface IStrategy
{
    void Algorithm();
}

public class ConcreteStrategyA : IStrategy
{
    public void Algorithm()
    {
        Console.WriteLine("Algorithm A");
    }
}

public class ConcreteStrategyB : IStrategy
{
    public void Algorithm()
    {
        Console.WriteLine("Algorithm B");
    }
}

public class Context
{
    private IStrategy _strategy;

    public Context(IStrategy strategy)
    {
        _strategy = strategy;
    }

    public void ExecuteStrategy()
    {
        _strategy.Algorithm();
    }
}

// Usage
Context context = new Context(new ConcreteStrategyA());
context.ExecuteStrategy();
context = new Context(new ConcreteStrategyB());
context.ExecuteStrategy();
```

---

**15. What is the Command pattern?**
**Answer:** The Command pattern encapsulates a request as an object, thereby allowing for parameterizing clients with queues, requests, and operations. It also provides support for undoable operations.

**Example:**
```csharp
public interface ICommand
{
    void Execute();
}

public class Light
{
    public void TurnOn()
    {
        Console.WriteLine("Light is on");
    }

    public void TurnOff()
    {
        Console.WriteLine("Light is off");
    }
}

public class LightOnCommand : ICommand
{
    private Light _light;

    public LightOnCommand(Light light)
    {
        _light = light;
    }

    public void Execute()
    {
        _light.TurnOn();
    }
}

public class LightOffCommand : ICommand
{
    private Light _light;

    public LightOffCommand(Light light)
    {
        _light = light;
    }

    public void Execute()
    {
        _light.TurnOff();
    }
}

public class RemoteControl
{
    private ICommand _command;

    public void SetCommand(ICommand command)
    {
        _command = command;
    }

    public void PressButton()
    {
        _command.Execute();
    }
}

// Usage
Light light = new Light();
ICommand lightOn = new LightOnCommand(light);
ICommand lightOff = new LightOffCommand(light);

RemoteControl remote = new RemoteControl();
remote.SetCommand(lightOn);
remote.PressButton();
remote.SetCommand(lightOff);
remote.PressButton();
```

---

**16. What is the Chain of Responsibility pattern?**
**Answer:** The Chain of Responsibility pattern creates a chain of receiver objects for a request. It decouples the sender and receiver by giving multiple objects a chance to handle the request.

**Example:**
```csharp
public abstract class Handler
{
    protected Handler _successor;

    public void SetSuccessor(Handler successor)
    {
        _successor = successor;
    }

    public abstract void HandleRequest(int request);
}

public class ConcreteHandler1 : Handler
{
    public override void HandleRequest(int request)
    {
        if (request < 10)
        {
            Console.WriteLine($"{GetType().Name} handled request {request}");
        }
        else if (_successor != null)
        {
            _successor.HandleRequest(request);
        }
    }
}

public class ConcreteHandler2 : Handler
{
    public override void HandleRequest(int request)
    {
        if (request >= 10 && request < 20)
        {
            Console.WriteLine($"{GetType().Name} handled request {request}");
        }
        else if (_successor != null)
        {
            _successor.HandleRequest(request);
        }
    }
}

// Usage
Handler handler1 = new ConcreteHandler1();
Handler handler2 = new ConcreteHandler2();

handler1.SetSuccessor(handler2);

int[] requests = { 5, 14, 22, 18, 3, 27, 20 };

foreach (int request in requests)
{
    handler1.HandleRequest(request);
}
```

---

**17. What is the Mediator pattern?**
**Answer:** The Mediator pattern defines an object that encapsulates how a set of objects interact. This pattern promotes loose coupling by keeping objects from referring to each other explicitly, allowing their interaction to vary independently.

**Example:**
```csharp
public interface IMediator
{
    void Send(string message, Colleague colleague);
}

public abstract class Colleague
{
    protected IMediator mediator;

    public Colleague(IMediator mediator)
    {
        this.mediator = mediator;
    }
}

public class ConcreteColleague1 : Colleague
{
    public ConcreteColleague1(IMediator mediator) : base(mediator) { }

    public void Send(string message)
    {
        mediator.Send(message, this);
    }

    public void Notify(string message)
    {
        Console.WriteLine($"Colleague1 receives message: {message}");
    }
}

public class ConcreteColleague2 : Colleague
{
    public ConcreteColleague2(IMediator mediator) : base(mediator) { }

    public void Send(string message)
    {
        mediator.Send(message, this);
    }

    public void Notify(string message)
    {
        Console.WriteLine($"Colleague2 receives message: {message}");
    }
}

public class ConcreteMediator : IMediator
{
    private ConcreteColleague1 _colleague1;
    private ConcreteColleague2 _colleague2;

    public ConcreteColleague1 Colleague1
    {
        set { _colleague1 = value; }
    }

    public ConcreteColleague2 Colleague2
    {
        set { _colleague2 = value; }
    }

    public void Send(string message, Colleague colleague)
    {
        if (colleague == _colleague1)
        {
            _colleague2.Notify(message);
        }
        else
        {
            _colleague1.Notify(message);
        }
    }
}

// Usage
ConcreteMediator mediator = new ConcreteMediator();

ConcreteColleague1 colleague1 = new ConcreteColleague1(mediator);
ConcreteColleague2 colleague2 = new ConcreteColleague2(mediator);

mediator.Colleague1 = colleague1;
mediator.Colleague2 = colleague2;

colleague1.Send("Hello from Colleague1");
colleague2.Send("Hello from Colleague2");
```

---

**18. What is the State pattern?**
**Answer:** The State pattern allows an object to alter its behavior when its internal state changes. The object will appear to change its class.

**Example:**
```csharp
public interface IState
{
    void Handle(Context context);
}

public class ConcreteStateA : IState
{
    public void Handle(Context context)
    {
        Console.WriteLine("Handling request by ConcreteStateA.");
        context.State = new ConcreteStateB();
    }
}

public class ConcreteStateB : IState
{
    public void Handle(Context context)
    {
        Console.WriteLine("

Handling request by ConcreteStateB.");
        context.State = new ConcreteStateA();
    }
}

public class Context
{
    private IState _state;

    public Context(IState state)
    {
        State = state;
    }

    public IState State
    {
        get { return _state; }
        set
        {
            _state = value;
            Console.WriteLine($"State changed to {value.GetType().Name}");
        }
    }

    public void Request()
    {
        _state.Handle(this);
    }
}

// Usage
Context context = new Context(new ConcreteStateA());
context.Request();
context.Request();
```

---

**19. What is the Memento pattern?**
**Answer:** The Memento pattern provides the ability to restore an object to its previous state. It is used to capture and externalize an object's internal state so that it can be restored later without violating encapsulation.

**Example:**
```csharp
public class Memento
{
    public string State { get; private set; }

    public Memento(string state)
    {
        State = state;
    }
}

public class Originator
{
    public string State { get; set; }

    public Memento SaveState()
    {
        return new Memento(State);
    }

    public void RestoreState(Memento memento)
    {
        State = memento.State;
    }
}

public class Caretaker
{
    private List<Memento> _mementos = new List<Memento>();
    private Originator _originator;

    public Caretaker(Originator originator)
    {
        _originator = originator;
    }

    public void Save()
    {
        _mementos.Add(_originator.SaveState());
    }

    public void Undo()
    {
        if (_mementos.Count > 0)
        {
            var memento = _mementos[^1];
            _mementos.RemoveAt(_mementos.Count - 1);
            _originator.RestoreState(memento);
        }
    }
}

// Usage
Originator originator = new Originator();
Caretaker caretaker = new Caretaker(originator);

originator.State = "State1";
caretaker.Save();

originator.State = "State2";
caretaker.Save();

originator.State = "State3";

caretaker.Undo();
Console.WriteLine($"Restored State: {originator.State}");
caretaker.Undo();
Console.WriteLine($"Restored State: {originator.State}");
```

---

**20. What is the Visitor pattern?**
**Answer:** The Visitor pattern allows adding further operations to objects without having to modify them. It separates an algorithm from the object structure it operates on, enabling new operations to be added without changing the classes of the elements on which it operates.

**Example:**
```csharp
public interface IVisitor
{
    void VisitConcreteElementA(ConcreteElementA elementA);
    void VisitConcreteElementB(ConcreteElementB elementB);
}

public abstract class Element
{
    public abstract void Accept(IVisitor visitor);
}

public class ConcreteElementA : Element
{
    public override void Accept(IVisitor visitor)
    {
        visitor.VisitConcreteElementA(this);
    }

    public void OperationA()
    {
        Console.WriteLine("ConcreteElementA operation");
    }
}

public class ConcreteElementB : Element
{
    public override void Accept(IVisitor visitor)
    {
        visitor.VisitConcreteElementB(this);
    }

    public void OperationB()
    {
        Console.WriteLine("ConcreteElementB operation");
    }
}

public class ConcreteVisitor : IVisitor
{
    public void VisitConcreteElementA(ConcreteElementA elementA)
    {
        elementA.OperationA();
    }

    public void VisitConcreteElementB(ConcreteElementB elementB)
    {
        elementB.OperationB();
    }
}

// Usage
List<Element> elements = new List<Element>
{
    new ConcreteElementA(),
    new ConcreteElementB()
};

IVisitor visitor = new ConcreteVisitor();

foreach (var element in elements)
{
    element.Accept(visitor);
}
```

---

