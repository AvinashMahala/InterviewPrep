Sure, here are 100 questions covering Programming Languages (C#, Python, JavaScript, TypeScript) and Databases (MongoDB, MS SQL, MySQL):

### C#

1. **Question:** What is C# and what are its primary features?
   - **Answer:** C# is a modern, object-oriented programming language developed by Microsoft. Its primary features include strong typing, imperative, declarative, functional, generic, and component-oriented programming disciplines.

2. **Question:** How do you create a class in C#?
   - **Answer:** A class in C# is created using the `class` keyword followed by the class name and body.
   ```csharp
   public class MyClass
   {
       public int MyProperty { get; set; }
   }
   ```

3. **Question:** What are properties in C# and how are they used?
   - **Answer:** Properties in C# are members that provide a flexible mechanism to read, write, or compute the values of private fields. They use `get` and `set` accessors.
   ```csharp
   public class MyClass
   {
       private int _myField;
       public int MyProperty
       {
           get { return _myField; }
           set { _myField = value; }
       }
   }
   ```

4. **Question:** How do you implement inheritance in C#?
   - **Answer:** Inheritance in C# is implemented by using the `:` symbol followed by the base class name.
   ```csharp
   public class BaseClass
   {
       public void BaseMethod() { }
   }

   public class DerivedClass : BaseClass
   {
       public void DerivedMethod() { }
   }
   ```

5. **Question:** What is polymorphism in C# and how is it achieved?
   - **Answer:** Polymorphism in C# allows methods to do different things based on the object it is acting upon. It is achieved using method overriding and interfaces.
   ```csharp
   public class BaseClass
   {
       public virtual void Display()
       {
           Console.WriteLine("Base Display");
       }
   }

   public class DerivedClass : BaseClass
   {
       public override void Display()
       {
           Console.WriteLine("Derived Display");
       }
   }
   ```

6. **Question:** How do you handle exceptions in C#?
   - **Answer:** Exceptions in C# are handled using try-catch blocks. The `try` block contains the code that may cause an exception, and the `catch` block contains the code to handle the exception.
   ```csharp
   try
   {
       // Code that may throw an exception
   }
   catch (Exception ex)
   {
       // Handle the exception
   }
   ```

7. **Question:** What is the difference between `ref` and `out` parameters in C#?
   - **Answer:** Both `ref` and `out` are used to pass arguments by reference. `ref` requires that the variable be initialized before being passed, while `out` does not require initialization but must be assigned a value before the method returns.

8. **Question:** What are delegates in C# and how are they used?
   - **Answer:** Delegates in C# are type-safe function pointers. They are used to encapsulate a method with a specific signature and return type.
   ```csharp
   public delegate void MyDelegate(string message);

   public class MyClass
   {
       public void PrintMessage(string message)
       {
           Console.WriteLine(message);
       }
   }
   ```

9. **Question:** How do you create and use events in C#?
   - **Answer:** Events in C# are created using the `event` keyword and are based on delegates.
   ```csharp
   public class MyClass
   {
       public event EventHandler MyEvent;

       protected virtual void OnMyEvent()
       {
           if (MyEvent != null)
               MyEvent(this, EventArgs.Empty);
       }
   }
   ```

10. **Question:** What is LINQ in C# and how is it used?
    - **Answer:** LINQ (Language Integrated Query) in C# is used to perform queries on collections. It provides a consistent syntax to query various data sources.
    ```csharp
    int[] numbers = { 1, 2, 3, 4, 5 };
    var evenNumbers = from num in numbers
                      where num % 2 == 0
                      select num;
    ```

### Python

11. **Question:** What is Python and what are its primary features?
    - **Answer:** Python is an interpreted, high-level, general-purpose programming language known for its readability, simplicity, and versatility. Primary features include dynamic typing, memory management, and extensive standard libraries.

12. **Question:** How do you create a function in Python?
    - **Answer:** A function in Python is created using the `def` keyword followed by the function name and parameters.
    ```python
    def my_function(param):
        return param * 2
    ```

13. **Question:** What are Python decorators and how are they used?
    - **Answer:** Decorators in Python are functions that modify the behavior of other functions or methods. They are used with the `@decorator` syntax.
    ```python
    def my_decorator(func):
        def wrapper():
            print("Something is happening before the function is called.")
            func()
            print("Something is happening after the function is called.")
        return wrapper

    @my_decorator
    def say_hello():
        print("Hello!")
    ```

14. **Question:** How do you handle exceptions in Python?
    - **Answer:** Exceptions in Python are handled using try-except blocks. The `try` block contains the code that may cause an exception, and the `except` block contains the code to handle the exception.
    ```python
    try:
        # Code that may throw an exception
    except Exception as e:
        # Handle the exception
    ```

15. **Question:** What is the difference between a list and a tuple in Python?
    - **Answer:** Lists in Python are mutable, meaning their elements can be changed, whereas tuples are immutable, meaning their elements cannot be changed once assigned.

16. **Question:** How do you create a class in Python?
    - **Answer:** A class in Python is created using the `class` keyword followed by the class name and a colon.
    ```python
    class MyClass:
        def __init__(self, param):
            self.param = param

        def my_method(self):
            return self.param * 2
    ```

17. **Question:** What is list comprehension in Python and how is it used?
    - **Answer:** List comprehension in Python provides a concise way to create lists. It is used to generate lists from existing lists by applying an expression to each element.
    ```python
    numbers = [1, 2, 3, 4, 5]
    squares = [num * num for num in numbers]
    ```

18. **Question:** How do you use the `with` statement in Python?
    - **Answer:** The `with` statement in Python is used to wrap the execution of a block of code. It ensures proper acquisition and release of resources.
    ```python
    with open('file.txt', 'r') as file:
        content = file.read()
    ```

19. **Question:** What are Python generators and how are they used?
    - **Answer:** Generators in Python are functions that return an iterator using the `yield` keyword. They allow you to iterate over data without storing it all in memory.
    ```python
    def my_generator():
        yield 1
        yield 2
        yield 3

    for value in my_generator():
        print(value)
    ```

20. **Question:** How do you perform file I/O in Python?
    - **Answer:** File I/O in Python is performed using built-in functions like `open`, `read`, `write`, and `close`.
    ```python
    with open('file.txt', 'w') as file:
        file.write('Hello, world!')
    ```

### JavaScript

21. **Question:** What is JavaScript and what are its primary features?
    - **Answer:** JavaScript is a high-level, interpreted scripting language primarily used for creating dynamic web content. Primary features include first-class functions, dynamic typing, and prototypal inheritance.

22. **Question:** How do you create a function in JavaScript?
    - **Answer:** A function in JavaScript is created using the `function` keyword followed by the function name and parameters.
    ```javascript
    function myFunction(param) {
        return param * 2;
    }
    ```

23. **Question:** What is the difference between `let`, `const`, and `var` in JavaScript?
    - **Answer:** `let` and `const` are block-scoped, whereas `var` is function-scoped. `const` is used to declare constants, which cannot be reassigned.

24. **Question:** How do you handle asynchronous operations in JavaScript?
    - **Answer:** Asynchronous operations in JavaScript are handled using callbacks, promises, and the `async/await` syntax.
    ```javascript
    // Using Promises
    function fetchData() {
        return new Promise((resolve, reject) => {
            // Asynchronous operation
            resolve(data);
        });
    }

    // Using async/await
    async function getData() {
        const data = await fetchData();
        console.log(data);
    }
    ```

25. **Question:** What is the DOM in JavaScript?
    - **Answer:**

 The DOM (Document Object Model) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content.

26. **Question:** How do you select elements in the DOM using JavaScript?
    - **Answer:** Elements in the DOM are selected using methods like `getElementById`, `getElementsByClassName`, `getElementsByTagName`, `querySelector`, and `querySelectorAll`.
    ```javascript
    const element = document.getElementById('myElement');
    ```

27. **Question:** What are JavaScript closures and how are they used?
    - **Answer:** Closures in JavaScript are functions that have access to the variables in their outer scope, even after the outer function has returned.
    ```javascript
    function outerFunction() {
        let outerVariable = 'I am outside!';

        function innerFunction() {
            console.log(outerVariable);
        }

        return innerFunction;
    }

    const myClosure = outerFunction();
    myClosure();
    ```

28. **Question:** How do you handle events in JavaScript?
    - **Answer:** Events in JavaScript are handled using event listeners, which are attached to elements using methods like `addEventListener`.
    ```javascript
    document.getElementById('myButton').addEventListener('click', () => {
        console.log('Button clicked!');
    });
    ```

29. **Question:** What is the purpose of the `this` keyword in JavaScript?
    - **Answer:** The `this` keyword in JavaScript refers to the object that is currently executing the function. Its value depends on how the function is called.

30. **Question:** How do you perform JSON operations in JavaScript?
    - **Answer:** JSON operations in JavaScript are performed using the `JSON.parse` method to convert a JSON string to an object and the `JSON.stringify` method to convert an object to a JSON string.
    ```javascript
    const jsonString = '{"name": "John", "age": 30}';
    const obj = JSON.parse(jsonString);
    const newJsonString = JSON.stringify(obj);
    ```

### TypeScript

31. **Question:** What is TypeScript and what are its primary features?
    - **Answer:** TypeScript is a typed superset of JavaScript that compiles to plain JavaScript. Its primary features include static typing, classes, interfaces, and advanced tooling.

32. **Question:** How do you define a variable in TypeScript?
    - **Answer:** Variables in TypeScript are defined using `let`, `const`, or `var` with type annotations.
    ```typescript
    let myString: string = 'Hello, TypeScript';
    ```

33. **Question:** How do you create an interface in TypeScript?
    - **Answer:** An interface in TypeScript is created using the `interface` keyword followed by the interface name and body.
    ```typescript
    interface Person {
        name: string;
        age: number;
    }
    ```

34. **Question:** What are TypeScript enums and how are they used?
    - **Answer:** Enums in TypeScript are a way to define a set of named constants. They are created using the `enum` keyword.
    ```typescript
    enum Direction {
        Up,
        Down,
        Left,
        Right
    }
    ```

35. **Question:** How do you implement classes in TypeScript?
    - **Answer:** Classes in TypeScript are implemented using the `class` keyword and can include properties, constructors, and methods.
    ```typescript
    class Person {
        name: string;
        age: number;

        constructor(name: string, age: number) {
            this.name = name;
            this.age = age;
        }

        greet() {
            return `Hello, my name is ${this.name}`;
        }
    }
    ```

36. **Question:** What are TypeScript generics and how are they used?
    - **Answer:** Generics in TypeScript provide a way to create reusable components that can work with different data types. They are defined using angle brackets (`<>`).
    ```typescript
    function identity<T>(arg: T): T {
        return arg;
    }
    ```

37. **Question:** How do you handle modules in TypeScript?
    - **Answer:** Modules in TypeScript are handled using the `import` and `export` keywords. Files are considered modules if they have at least one `import` or `export` statement.
    ```typescript
    // module.ts
    export const myVariable = 'Hello, Module';

    // main.ts
    import { myVariable } from './module';
    ```

38. **Question:** What is the difference between `interface` and `type` in TypeScript?
    - **Answer:** Both `interface` and `type` can be used to define object shapes, but `type` can also be used to create union types, mapped types, and other advanced type constructs. `interface` is more extendable.

39. **Question:** How do you use the `readonly` modifier in TypeScript?
    - **Answer:** The `readonly` modifier in TypeScript is used to mark properties as read-only, meaning they can be assigned only once.
    ```typescript
    class Person {
        readonly name: string;

        constructor(name: string) {
            this.name = name;
        }
    }
    ```

40. **Question:** How do you perform type assertions in TypeScript?
    - **Answer:** Type assertions in TypeScript are performed using the `as` syntax or the angle bracket syntax.
    ```typescript
    let someValue: any = 'this is a string';
    let strLength: number = (someValue as string).length;
    ```

### MongoDB

41. **Question:** What is MongoDB and what are its primary features?
    - **Answer:** MongoDB is a NoSQL database known for its flexibility, scalability, and performance. Primary features include a document-oriented data model, distributed architecture, and rich query language.

42. **Question:** How do you create a database in MongoDB?
    - **Answer:** A database in MongoDB is created by switching to a non-existent database using the `use` command and inserting a document into a collection.
    ```shell
    use myDatabase
    db.myCollection.insertOne({ name: "John" })
    ```

43. **Question:** How do you insert a document into a MongoDB collection?
    - **Answer:** A document is inserted into a MongoDB collection using the `insertOne` or `insertMany` methods.
    ```shell
    db.myCollection.insertOne({ name: "John", age: 30 })
    ```

44. **Question:** How do you query documents in MongoDB?
    - **Answer:** Documents in MongoDB are queried using the `find` method with a query object.
    ```shell
    db.myCollection.find({ age: { $gt: 25 } })
    ```

45. **Question:** What are MongoDB indexes and how are they used?
    - **Answer:** Indexes in MongoDB are used to improve query performance. They are created using the `createIndex` method.
    ```shell
    db.myCollection.createIndex({ name: 1 })
    ```

46. **Question:** How do you update documents in MongoDB?
    - **Answer:** Documents in MongoDB are updated using the `updateOne` or `updateMany` methods with an update object.
    ```shell
    db.myCollection.updateOne({ name: "John" }, { $set: { age: 31 } })
    ```

47. **Question:** How do you delete documents in MongoDB?
    - **Answer:** Documents in MongoDB are deleted using the `deleteOne` or `deleteMany` methods.
    ```shell
    db.myCollection.deleteOne({ name: "John" })
    ```

48. **Question:** What is aggregation in MongoDB and how is it used?
    - **Answer:** Aggregation in MongoDB is used to process data records and return computed results. It is performed using the `aggregate` method with a pipeline of stages.
    ```shell
    db.myCollection.aggregate([
        { $match: { age: { $gt: 25 } } },
        { $group: { _id: "$name", total: { $sum: "$age" } } }
    ])
    ```

49. **Question:** How do you perform text search in MongoDB?
    - **Answer:** Text search in MongoDB is performed using a text index and the `$text` query operator.
    ```shell
    db.myCollection.createIndex({ name: "text" })
    db.myCollection.find({ $text: { $search: "John" } })
    ```

50. **Question:** What is sharding in MongoDB and how does it work?
    - **Answer:** Sharding in MongoDB is a method for distributing data across multiple machines. It splits data into smaller chunks and distributes them across shards for horizontal scalability.

### MS SQL

51. **Question:** What is MS SQL and what are its primary features?
    - **Answer:** MS SQL (Microsoft SQL Server) is a relational database management system developed by Microsoft. Its primary features include transaction processing, security, replication, and business intelligence tools.

52. **Question:** How do you create a database in MS SQL?
    - **Answer:** A database in MS SQL is created using the `CREATE DATABASE` statement.
    ```sql
    CREATE DATABASE myDatabase;
    ```

53. **Question:** How do you create a table in MS SQL?
    - **Answer:** A table in MS SQL is created using the `CREATE TABLE` statement.
    ```sql
   

 CREATE TABLE myTable (
        ID int PRIMARY KEY,
        Name nvarchar(50),
        Age int
    );
    ```

54. **Question:** How do you insert data into a table in MS SQL?
    - **Answer:** Data is inserted into a table in MS SQL using the `INSERT INTO` statement.
    ```sql
    INSERT INTO myTable (ID, Name, Age) VALUES (1, 'John', 30);
    ```

55. **Question:** How do you query data from a table in MS SQL?
    - **Answer:** Data is queried from a table in MS SQL using the `SELECT` statement.
    ```sql
    SELECT * FROM myTable WHERE Age > 25;
    ```

56. **Question:** How do you update data in a table in MS SQL?
    - **Answer:** Data in a table is updated in MS SQL using the `UPDATE` statement.
    ```sql
    UPDATE myTable SET Age = 31 WHERE ID = 1;
    ```

57. **Question:** How do you delete data from a table in MS SQL?
    - **Answer:** Data is deleted from a table in MS SQL using the `DELETE` statement.
    ```sql
    DELETE FROM myTable WHERE ID = 1;
    ```

58. **Question:** What are MS SQL indexes and how are they used?
    - **Answer:** Indexes in MS SQL are used to improve query performance by allowing faster retrieval of records. They are created using the `CREATE INDEX` statement.
    ```sql
    CREATE INDEX idx_name ON myTable (Name);
    ```

59. **Question:** How do you use transactions in MS SQL?
    - **Answer:** Transactions in MS SQL are used to ensure a series of operations are executed as a single unit. They are managed using `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` statements.
    ```sql
    BEGIN TRANSACTION;
    UPDATE myTable SET Age = 31 WHERE ID = 1;
    COMMIT;
    ```

60. **Question:** How do you perform joins in MS SQL?
    - **Answer:** Joins in MS SQL are used to combine rows from two or more tables based on a related column. Types of joins include INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.
    ```sql
    SELECT a.Name, b.OrderID
    FROM Customers a
    INNER JOIN Orders b ON a.CustomerID = b.CustomerID;
    ```

### MySQL

61. **Question:** What is MySQL and what are its primary features?
    - **Answer:** MySQL is an open-source relational database management system. Its primary features include high performance, scalability, replication, and strong data protection.

62. **Question:** How do you create a database in MySQL?
    - **Answer:** A database in MySQL is created using the `CREATE DATABASE` statement.
    ```sql
    CREATE DATABASE myDatabase;
    ```

63. **Question:** How do you create a table in MySQL?
    - **Answer:** A table in MySQL is created using the `CREATE TABLE` statement.
    ```sql
    CREATE TABLE myTable (
        ID int PRIMARY KEY,
        Name varchar(50),
        Age int
    );
    ```

64. **Question:** How do you insert data into a table in MySQL?
    - **Answer:** Data is inserted into a table in MySQL using the `INSERT INTO` statement.
    ```sql
    INSERT INTO myTable (ID, Name, Age) VALUES (1, 'John', 30);
    ```

65. **Question:** How do you query data from a table in MySQL?
    - **Answer:** Data is queried from a table in MySQL using the `SELECT` statement.
    ```sql
    SELECT * FROM myTable WHERE Age > 25;
    ```

66. **Question:** How do you update data in a table in MySQL?
    - **Answer:** Data in a table is updated in MySQL using the `UPDATE` statement.
    ```sql
    UPDATE myTable SET Age = 31 WHERE ID = 1;
    ```

67. **Question:** How do you delete data from a table in MySQL?
    - **Answer:** Data is deleted from a table in MySQL using the `DELETE` statement.
    ```sql
    DELETE FROM myTable WHERE ID = 1;
    ```

68. **Question:** What are MySQL indexes and how are they used?
    - **Answer:** Indexes in MySQL are used to improve query performance by allowing faster retrieval of records. They are created using the `CREATE INDEX` statement.
    ```sql
    CREATE INDEX idx_name ON myTable (Name);
    ```

69. **Question:** How do you use transactions in MySQL?
    - **Answer:** Transactions in MySQL are used to ensure a series of operations are executed as a single unit. They are managed using `START TRANSACTION`, `COMMIT`, and `ROLLBACK` statements.
    ```sql
    START TRANSACTION;
    UPDATE myTable SET Age = 31 WHERE ID = 1;
    COMMIT;
    ```

70. **Question:** How do you perform joins in MySQL?
    - **Answer:** Joins in MySQL are used to combine rows from two or more tables based on a related column. Types of joins include INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.
    ```sql
    SELECT a.Name, b.OrderID
    FROM Customers a
    INNER JOIN Orders b ON a.CustomerID = b.CustomerID;
    ```

### Advanced C#

71. **Question:** How do you implement async and await in C#?
    - **Answer:** `async` and `await` in C# are used to write asynchronous code more easily. An `async` method is marked with the `async` keyword, and the `await` keyword is used to wait for asynchronous operations.
    ```csharp
    public async Task<int> GetDataAsync()
    {
        await Task.Delay(1000); // Simulate an async operation
        return 42;
    }
    ```

72. **Question:** How do you use LINQ to query a collection in C#?
    - **Answer:** LINQ (Language Integrated Query) is used to query collections in C#. It uses a SQL-like syntax for querying data from various sources.
    ```csharp
    int[] numbers = { 1, 2, 3, 4, 5 };
    var evenNumbers = from num in numbers
                      where num % 2 == 0
                      select num;
    ```

73. **Question:** What are extension methods in C# and how are they used?
    - **Answer:** Extension methods in C# are static methods that extend the functionality of existing types. They are defined in static classes and use the `this` keyword in the parameter list.
    ```csharp
    public static class StringExtensions
    {
        public static int WordCount(this string str)
        {
            return str.Split(new char[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries).Length;
        }
    }
    ```

74. **Question:** How do you use lambda expressions in C#?
    - **Answer:** Lambda expressions in C# are used to create anonymous functions. They are often used with LINQ and other functional programming constructs.
    ```csharp
    Func<int, int, int> add = (x, y) => x + y;
    ```

75. **Question:** What is the `async` keyword in C# and how is it used?
    - **Answer:** The `async` keyword in C# is used to define asynchronous methods. It allows the use of the `await` keyword to asynchronously wait for tasks to complete.
    ```csharp
    public async Task<int> GetDataAsync()
    {
        await Task.Delay(1000); // Simulate an async operation
        return 42;
    }
    ```

76. **Question:** What is the `await` keyword in C# and how is it used?
    - **Answer:** The `await` keyword in C# is used to asynchronously wait for a task to complete. It can only be used within an `async` method.
    ```csharp
    public async Task<int> GetDataAsync()
    {
        await Task.Delay(1000); // Simulate an async operation
        return 42;
    }
    ```

77. **Question:** How do you implement a custom attribute in C#?
    - **Answer:** Custom attributes in C# are implemented by creating a class that inherits from `System.Attribute`.
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
    ```

78. **Question:** What are C# collections and how are they used?
    - **Answer:** C# collections are data structures used to store groups of related objects. Common collections include `List`, `Dictionary`, `HashSet`, and `Queue`.
    ```csharp
    List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
    Dictionary<string, int> ages = new Dictionary<string, int> { { "John", 30 }, { "Jane", 25 } };
    ```

79. **Question:** How do you use the `yield` keyword in C#?
    - **Answer:** The `yield` keyword in C# is used in an iterator method to return each element one at a time. It is used with `IEnumerable`

 or `IEnumerator`.
    ```csharp
    public IEnumerable<int> GetNumbers()
    {
        yield return 1;
        yield return 2;
        yield return 3;
    }
    ```

80. **Question:** How do you handle concurrency in C#?
    - **Answer:** Concurrency in C# is handled using tasks and parallel programming constructs like `Task`, `Parallel`, and `async`/`await`.
    ```csharp
    Task.Run(() =>
    {
        // Concurrent operation
    });
    ```

### Advanced Python

81. **Question:** How do you use decorators in Python?
    - **Answer:** Decorators in Python are functions that modify the behavior of other functions or methods. They are applied using the `@decorator` syntax.
    ```python
    def my_decorator(func):
        def wrapper():
            print("Something is happening before the function is called.")
            func()
            print("Something is happening after the function is called.")
        return wrapper

    @my_decorator
    def say_hello():
        print("Hello!")
    ```

82. **Question:** How do you use generators in Python?
    - **Answer:** Generators in Python are functions that return an iterator using the `yield` keyword. They allow you to iterate over data without storing it all in memory.
    ```python
    def my_generator():
        yield 1
        yield 2
        yield 3

    for value in my_generator():
        print(value)
    ```

83. **Question:** What is the `with` statement in Python and how is it used?
    - **Answer:** The `with` statement in Python is used to wrap the execution of a block of code. It ensures proper acquisition and release of resources.
    ```python
    with open('file.txt', 'r') as file:
        content = file.read()
    ```

84. **Question:** How do you perform file I/O in Python?
    - **Answer:** File I/O in Python is performed using built-in functions like `open`, `read`, `write`, and `close`.
    ```python
    with open('file.txt', 'w') as file:
        file.write('Hello, world!')
    ```

85. **Question:** How do you use list comprehensions in Python?
    - **Answer:** List comprehensions in Python provide a concise way to create lists. They are used to generate lists from existing lists by applying an expression to each element.
    ```python
    numbers = [1, 2, 3, 4, 5]
    squares = [num * num for num in numbers]
    ```

86. **Question:** How do you use the `map` function in Python?
    - **Answer:** The `map` function in Python applies a given function to each item of an iterable and returns a list of the results.
    ```python
    numbers = [1, 2, 3, 4, 5]
    squares = list(map(lambda x: x * x, numbers))
    ```

87. **Question:** How do you use the `filter` function in Python?
    - **Answer:** The `filter` function in Python constructs an iterator from elements of an iterable for which a function returns true.
    ```python
    numbers = [1, 2, 3, 4, 5]
    even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
    ```

88. **Question:** How do you use the `reduce` function in Python?
    - **Answer:** The `reduce` function in Python performs a rolling computation to sequential pairs of values in a list. It is part of the `functools` module.
    ```python
    from functools import reduce
    numbers = [1, 2, 3, 4, 5]
    product = reduce((lambda x, y: x * y), numbers)
    ```

89. **Question:** How do you handle exceptions in Python?
    - **Answer:** Exceptions in Python are handled using try-except blocks. The `try` block contains the code that may cause an exception, and the `except` block contains the code to handle the exception.
    ```python
    try:
        # Code that may throw an exception
    except Exception as e:
        # Handle the exception
    ```

90. **Question:** How do you use the `collections` module in Python?
    - **Answer:** The `collections` module in Python provides specialized container data types like `Counter`, `deque`, `namedtuple`, and `defaultdict`.
    ```python
    from collections import Counter
    count = Counter([1, 2, 2, 3, 3, 3])
    ```

### Advanced JavaScript

91. **Question:** What are JavaScript promises and how are they used?
    - **Answer:** Promises in JavaScript represent the eventual completion (or failure) of an asynchronous operation. They are used to handle asynchronous operations more effectively.
    ```javascript
    let promise = new Promise((resolve, reject) => {
        // Asynchronous operation
        resolve('Success!');
    });

    promise.then(result => console.log(result)).catch(error => console.error(error));
    ```

92. **Question:** How do you use the `fetch` API in JavaScript?
    - **Answer:** The `fetch` API in JavaScript is used to make network requests. It returns a promise that resolves to the response object.
    ```javascript
    fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => console.log(data))
        .catch(error => console.error('Error:', error));
    ```

93. **Question:** How do you create classes in JavaScript ES6?
    - **Answer:** Classes in JavaScript ES6 are created using the `class` keyword, which provides a cleaner syntax for creating objects and dealing with inheritance.
    ```javascript
    class Person {
        constructor(name, age) {
            this.name = name;
            this.age = age;
        }

        greet() {
            console.log(`Hello, my name is ${this.name}`);
        }
    }
    ```

94. **Question:** How do you use modules in JavaScript ES6?
    - **Answer:** Modules in JavaScript ES6 are used to organize code into reusable pieces. The `export` keyword is used to export functions, objects, or primitives from a module, and the `import` keyword is used to import them.
    ```javascript
    // module.js
    export const myVariable = 'Hello, Module';

    // main.js
    import { myVariable } from './module.js';
    ```

95. **Question:** What is the `async` keyword in JavaScript and how is it used?
    - **Answer:** The `async` keyword in JavaScript is used to define asynchronous functions. It allows the use of the `await` keyword to wait for promises to resolve.
    ```javascript
    async function getData() {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        console.log(data);
    }
    ```

96. **Question:** How do you use the `await` keyword in JavaScript?
    - **Answer:** The `await` keyword in JavaScript is used to pause the execution of an `async` function until a promise is resolved or rejected.
    ```javascript
    async function getData() {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        console.log(data);
    }
    ```

97. **Question:** What are JavaScript arrow functions and how are they used?
    - **Answer:** Arrow functions in JavaScript provide a shorter syntax for writing function expressions and do not have their own `this` context.
    ```javascript
    const add = (a, b) => a + b;
    ```

98. **Question:** How do you use the `Map` object in JavaScript?
    - **Answer:** The `Map` object in JavaScript holds key-value pairs and remembers the original insertion order of the keys.
    ```javascript
    let map = new Map();
    map.set('name', 'John');
    console.log(map.get('name')); // John
    ```

99. **Question:** How do you use the `Set` object in JavaScript?
    - **Answer:** The `Set` object in JavaScript lets you store unique values of any type, whether primitive values or object references.
    ```javascript
    let set = new Set([1, 2, 3, 3, 4]);
    console.log(set); // Set(4) {1, 2, 3, 4}
    ```

100. **Question:** How do you use the `reduce` method in JavaScript?
    - **Answer:** The `reduce` method in JavaScript executes a reducer function on each element of the array, resulting in a single output value.
    ```javascript
    let numbers = [1, 2, 3, 4, 5];
    let sum = numbers.reduce((total, current) => total + current, 0);
    ```

---

These questions cover various aspects of programming languages (C#, Python, JavaScript, TypeScript) and databases (MongoDB, MS SQL, MySQL), providing a comprehensive understanding of their features, configurations, and best practices.