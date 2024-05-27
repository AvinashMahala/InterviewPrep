### C# Interview Questions and Answers:

1. **What are the fundamental principles of object-oriented programming (OOP)?**
   - **Answer:**
     The four fundamental principles of OOP are:
     1. **Encapsulation:** Bundling the data (attributes) and methods (functions) that manipulate the data into a single unit called a class.
     2. **Abstraction:** Hiding the complex implementation details and showing only the essential features of the object.
     3. **Inheritance:** Creating new classes from existing classes, allowing code reuse and the creation of hierarchical relationships.
     4. **Polymorphism:** Allowing objects to be treated as instances of their parent class rather than their actual class, enabling one interface to be used for a general class of actions.

2. **Explain the difference between value types and reference types in C#.**
   - **Answer:**
     - **Value Types:** Stored in the stack, they hold the actual data. Examples include `int`, `float`, `char`, `struct`, and `enum`.
     - **Reference Types:** Stored in the heap, they hold a reference to the data's memory address. Examples include `class`, `interface`, `delegate`, `object`, and `string`.

3. **What is the purpose of the `using` statement in C#?**
   - **Answer:**
     The `using` statement is used to ensure that `IDisposable` objects are properly disposed of once they are no longer needed. It is used to manage resources like file handles, database connections, etc., ensuring that they are closed and released promptly.

4. **How does garbage collection work in C#?**
   - **Answer:**
     Garbage collection in C# is an automatic memory management feature that reclaims memory occupied by objects that are no longer in use. The garbage collector runs periodically, identifying and freeing up memory by destroying objects that are no longer reachable in the application.

5. **What are delegates and how are they used?**
   - **Answer:**
     Delegates are type-safe function pointers used to encapsulate a method. They are used to pass methods as arguments to other methods, define callback methods, and implement event handling.

6. **Explain the concept of LINQ and provide an example of its usage.**
   - **Answer:**
     LINQ (Language-Integrated Query) is a set of features that allows querying data in a type-safe manner using C# syntax. It can be used to query collections, databases, XML, and more.
     - **Example:**
       ```csharp
       List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
       var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();
       ```

7. **What is the difference between `IEnumerable` and `IQueryable`?**
   - **Answer:**
     - **`IEnumerable`:** Used for in-memory collections and executes the query when iterated over. It does not support remote querying.
     - **`IQueryable`:** Extends `IEnumerable` and is used for querying data from out-of-memory sources like databases. It supports remote querying and can be used with LINQ to SQL or Entity Framework to generate SQL queries.

8. **How do you handle exceptions in C#?**
   - **Answer:**
     Exceptions are handled using `try`, `catch`, and `finally` blocks. `try` contains the code that may throw an exception, `catch` handles the exception, and `finally` executes code that needs to run regardless of whether an exception occurred.
     ```csharp
     try
     {
         // Code that may throw an exception
     }
     catch (Exception ex)
     {
         // Handle exception
     }
     finally
     {
         // Code that runs regardless of exception
     }
     ```

9. **What is the `async` and `await` keyword used for in C#?**
   - **Answer:**
     `async` and `await` are used for asynchronous programming. The `async` keyword is used to declare a method as asynchronous, and the `await` keyword is used to asynchronously wait for a task to complete without blocking the main thread.
     ```csharp
     public async Task<int> GetDataAsync()
     {
         await Task.Delay(1000); // Simulate a delay
         return 42;
     }
     ```

10. **Explain the concept of extension methods in C#.**
    - **Answer:**
      Extension methods allow adding new methods to existing types without modifying the original type. They are static methods defined in static classes and use the `this` keyword in their first parameter to specify the type they extend.
      ```csharp
      public static class StringExtensions
      {
          public static int WordCount(this string str)
          {
              return str.Split(new[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries).Length;
          }
      }

      string text = "Hello, world!";
      int count = text.WordCount();
      ```

11. **What is dependency injection and how is it implemented in C#?**
    - **Answer:**
      Dependency injection (DI) is a design pattern that allows a class to receive its dependencies from an external source rather than creating them itself. It is implemented using constructors, properties, or method injection.
      ```csharp
      public class MyService
      {
          private readonly IMyDependency _dependency;

          public MyService(IMyDependency dependency)
          {
              _dependency = dependency;
          }

          public void DoWork()
          {
              _dependency.Execute();
          }
      }
      ```

12. **How do you create and use attributes in C#?**
    - **Answer:**
      Attributes are used to add metadata to code elements (classes, methods, properties, etc.). Custom attributes are created by inheriting from the `System.Attribute` class.
      ```csharp
      [AttributeUsage(AttributeTargets.Class | AttributeTargets.Method)]
      public class MyCustomAttribute : Attribute
      {
          public string Description { get; }

          public MyCustomAttribute(string description)
          {
              Description = description;
          }
      }

      [MyCustomAttribute("This is a custom attribute.")]
      public class MyClass
      {
      }
      ```

13. **What is the difference between abstract classes and interfaces?**
    - **Answer:**
      - **Abstract Classes:** Can contain implementation and abstract methods. They can have fields, properties, and constructors. They support inheritance and can only be inherited by a single class.
      - **Interfaces:** Only contain method signatures without implementations. They cannot have fields or constructors. A class can implement multiple interfaces.

14. **Explain the purpose of the `sealed` keyword in C#.**
    - **Answer:**
      The `sealed` keyword is used to prevent a class from being inherited. It can also be used to prevent a method from being overridden in derived classes.
      ```csharp
      public sealed class MyClass
      {
      }

      public class MyBaseClass
      {
          public virtual void MyMethod() { }
      }

      public class MyDerivedClass : MyBaseClass
      {
          public sealed override void MyMethod() { }
      }
      ```

15. **What is the difference between `lock`, `Monitor`, and `Mutex` in C#?**
    - **Answer:**
      - **`lock`:** A shorthand for `Monitor.Enter` and `Monitor.Exit`. It is used to ensure that only one thread can access a critical section of code at a time.
      - **`Monitor`:** Provides a more flexible way to acquire and release locks, with methods for entering, exiting, waiting, and signaling.
      - **`Mutex`:** A synchronization primitive used to manage access to a resource across multiple processes.

16. **How do you implement custom events in C#?**
    - **Answer:**
      Custom events are implemented using delegates and the `event` keyword.
      ```csharp
      public delegate void MyEventHandler(object sender, EventArgs e);

      public class MyPublisher
      {
          public event MyEventHandler MyEvent;

          protected virtual void OnMyEvent(EventArgs e)
          {
              MyEvent?.Invoke(this, e);
          }

          public void RaiseEvent()
          {
              OnMyEvent(EventArgs.Empty);
          }
      }
      ```

17. **What is reflection and how is it used in C#?**
    - **Answer:**
      Reflection allows inspecting and interacting with types and their members (methods, properties, fields) at runtime. It is used for tasks like dynamic type creation, method invocation, and accessing metadata.
      ```csharp
      Type type = typeof(MyClass);
      MethodInfo method = type.GetMethod("MyMethod");
      object instance = Activator.CreateInstance(type);
      method.Invoke(instance, null);
      ```

18. **How do you work with files in C#?**
    - **Answer:**
      The `System.IO` namespace provides classes for working with files, such as `File`, `FileStream`, `StreamReader`, and `StreamWriter`.
      ```csharp
      string path = "example.txt";
      File.WriteAllText(path, "Hello, world!");
      string content = File.ReadAllText(path);
      ```

19. **Explain the concept of anonymous methods and lambda expressions in C#.**
    - **Answer:**
      - **Anonymous Methods:** Methods without a name, defined using the `delegate` keyword. They are often used as inline event handlers or passed as arguments.
      - **Lambda Expressions:** Concise syntax for anonymous methods, using the `=>` operator.
      ```csharp
      Func<int, int> square = delegate (int x) {

 return x * x; };
      Func<int, int> squareLambda = x => x * x;
      ```

20. **What are async streams and how do you use them in C#?**
    - **Answer:**
      Async streams allow asynchronous iteration over a sequence of data. They are implemented using the `IAsyncEnumerable<T>` interface and the `await foreach` statement.
      ```csharp
      public async IAsyncEnumerable<int> GetNumbersAsync()
      {
          for (int i = 0; i < 10; i++)
          {
              await Task.Delay(100);
              yield return i;
          }
      }

      public async Task ConsumeAsync()
      {
          await foreach (int number in GetNumbersAsync())
          {
              Console.WriteLine(number);
          }
      }
      ```
