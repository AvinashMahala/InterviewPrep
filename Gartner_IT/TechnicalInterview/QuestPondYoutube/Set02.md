## Part 2 - Questions on Delegates, Event & Delegates vs Events.

**Common Responses**:
1. Delegates are used for callbacks.
2. Delegates are pointers to functions.

**Explaining Delegates**:
- **Delegates as Pointers**: This means a delegate can point to a method and invoke it. However, just saying a delegate is a pointer to a function can be misleading and doesn't fully capture its use.
- **Callbacks with Delegates**: More importantly, delegates are used for callbacks, particularly in asynchronous or multi-threaded environments.

**Creating a Delegate**:
```csharp
public delegate void SomeDelegate();
public static void Fun1() {
    Console.WriteLine("Hello");
}
SomeDelegate del = Fun1;
del.Invoke();
```
Here, the delegate points to the `Fun1` method and invokes it.

**Practical Use Case**:
- **Multi-threading and Callbacks**: Imagine a scenario where you have multiple threads running and you want to communicate between them.

**Example**:
1. **Create a Class with a Long-running Method**:
```csharp
public class SomeClass {
    public void HugeProcess() {
        for (int i = 0; i < 10000; i++) {
            Thread.Sleep(5000); // Simulating a long process
            // Callback to update the main thread
        }
    }
}
```
2. **Main Method**:
```csharp
SomeClass obj = new SomeClass();
Thread t = new Thread(new ThreadStart(obj.HugeProcess));
t.Start();
Console.WriteLine("Main thread continues...");
```
3. **Using Delegates for Callbacks**:
```csharp
public delegate void ProgressCallback(int progress);
public class SomeClass {
    public ProgressCallback Callback { get; set; }
    public void HugeProcess() {
        for (int i = 0; i < 10000; i++) {
            Thread.Sleep(5000);
            Callback?.Invoke(i);
        }
    }
}
// Main method
SomeClass obj = new SomeClass();
obj.Callback = new ProgressCallback(UpdateProgress);
Thread t = new Thread(new ThreadStart(obj.HugeProcess));
t.Start();
Console.WriteLine("Main thread continues...");
public static void UpdateProgress(int progress) {
    Console.WriteLine($"Progress: {progress}");
}
```

**Multicast Delegates**:
- **Adding Multiple Handlers**:
```csharp
public delegate void Notify();
public static void Handler1() {
    Console.WriteLine("Handler 1");
}
public static void Handler2() {
    Console.WriteLine("Handler 2");
}
Notify del = Handler1;
del += Handler2;
del.Invoke();
```
Here, both `Handler1` and `Handler2` are invoked.

**Events**:
- **Encapsulating Delegates**: Events prevent clients from manipulating the delegate directly.
```csharp
public delegate void Notify();
public class Process {
    public event Notify OnNotify;
    public void StartProcess() {
        // Simulate process
        OnNotify?.Invoke();
    }
}
public class Program {
    public static void Main() {
        Process process = new Process();
        process.OnNotify += Handler1;
        process.OnNotify += Handler2;
        process.StartProcess();
    }
    public static void Handler1() {
        Console.WriteLine("Handler 1");
    }
    public static void Handler2() {
        Console.WriteLine("Handler 2");
    }
}
```

**Summary**:
- **Delegates**: Used for callbacks, particularly in multi-threaded environments.
- **Multicast Delegates**: Allow multiple methods to be called.
- **Events**: Encapsulate delegates to provide a publisher-subscriber model.

**Tips**:
1. Start with the concept of callbacks to understand delegates.
2. Understand multicast delegates before moving to events.
3. Events provide a safe way to use delegates in a publisher-subscriber model.

**Interactive Questions**:
Feel free to ask questions or share scenarios where you've used delegates and events.

**Closing**:
Thank you for participating. Don't forget to share this session and suggest topics for future discussions. Visit questpond.com for more tutorials. Happy coding!