# C Sharp

What is c#...(TODO)

## Struct vs Class

| Struct                                                                    | Class                                            |
|---------------------------------------------------------------------------|--------------------------------------------------|
| Cannot have default constructor                                           | Has a default constructor                        |
| Are call by value                                                         | Are call by reference                            |
| New object can be created without `new` keyword                           | To create a new object `new` keyword is required |
| Inheritance is not supported                                              | Can inherit or be inherited by another call      |
| All members are public                                                    | Members can be public private or protected       |
| Static members are allowed                                                | Static members are allowed                       |
| `abstract` and `virtual` keywords are not allowed.                        | `abstract` and `virtual` keywords are allowed.   |
| `override` is allowed only when methods inherited from `System.ValueType` | `override` keyword is allowed.                   |


## Constructors

Constructor is a function that is run once for a objects lifetime that is when it is created. It is usually used to initialize the object.
Constructor will always have the same name as the class, it doesn't have a return-type and access-modifiers are optional.
There are 3 types of constructor:
- **Default**: It is a constructor that has no parameters.
- **Parameterized**: It is a constructor with at-least 1 or more arguments.
- **Static**: It is a constructor marked with static access-modifier and is invoked only once during the first reference of its static member.


## Properties + Getters and Setters (TODO)

## Out vs Ref

Both `out` and `ref` keyword are used to pass argument by reference. Properties are not variables hence cannot be used with `out` and `ref` keywords.

| Out                                                                             | Ref                                                                                 |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| argument to be passed as out, it is not mandatory to initialize it.             | ref variable must be initialized before passing the argument                        |
| inside the method it is mandatory to assign or modify the value of out argument | inside the method it is not mandatory to assign or modify the value of ref argument |
| out can only be used uni-directionally                                          | ref can be used bidirectionally                                                     |
| out is treated at runtime and doesn't change the method signature               | ref changes method signature as it affects type of the argument                     |


## Const vs Read-Only

| const                                          | read-only                                                        |
|------------------------------------------------|------------------------------------------------------------------|
| Const is a compile time constant.              | ReadOnly is a runtime constant.                                  |
| We can only assign values in declaration part. | We can assign values in declaration and in the constructor part. |
| It can be declared inside the method.          | It cannot be declared inside the method.                         |
| It cannot be used with static modifiers.       | It can be used with static modifiers.                            |

## Extension Methods

Extension methods are static methods but are called by using instance method syntax. They are used to add functionality of a class without the modifying the class itself.
Their first parameter specifies which type the method operates on. The parameter follows the this modifier.
Extension methods are only in scope when you explicitly import the namespace into your source code with a using directive.

**Example**:
```cs
namespace ExtensionMethods
{
    public static class MyExtensions
    {
        public static int WordCount(this string str)
        {
            return str.Split(new char[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries)
                .Length;
        }
    }
}
```

## Try Catch Finally

`try` statement can be used in the following forms:
- try-catch
- try-finally
- try-catch-finally

The `try` block is used to run unstable code that is likely to throw exceptions.

The `catch` statement is used to handle exceptions. If a `catch` block is specified and an exception is thrown the execution jumps to the catch block.
When using a try-catch statement; we can add multiple catch block and also use the when expression to filter exception to the correct catch block.
```cs
try
{
    var result = Process(-3, 4);
    Console.WriteLine($"Processing succeeded: {result}");
}
catch (Exception e) when (e is ArgumentException || e is DivideByZeroException)
{
    Console.WriteLine($"Processing failed: {e.Message}");
}
```

Lastly the `finally` statement runs after the try/catch blocks. It is an optional block `finally` is used to cleanup any resources or handlers allocated and used in the try block.
The finally block is guaranteed to run after try/catch block.


## Destructor & Disposable

## Delegates

A `delegate` is a type that represents references to methods with a particular parameter list and return type. You can say it is a type the represents the signature of functions & methods.

When you instantiate a delegate, you can associate its instance with compatible methods & functions.
You can invoke (or call) the method through the delegate instance.

**Example**
```cs
public delegate void Callback(string message);

// Create a method for a delegate.
public static void DelegateMethod(string message)
{
    Console.WriteLine(message);
}

// Instantiate the delegate.
Callback handler = DelegateMethod;

// Call the delegate.
handler("Hello World");

```


## Generics Type `<T>`

Generics introduces the concept of type parameters to .NET. Generics make it possible to design classes and methods that defer the specification of one or more type parameters until you use the class or method in your code.
This allows a class or method to be used by multiple types.

```cs
public class SimpleGenericClass<T>
{
    public T Field;
}
```

Advantages and disadvantages of generics

| Advantages                                                                                                                                                                                                                                                                                                                                                           | Disadvantages                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Type safety. Generics shift the burden of type safety from you to the compiler. There is no need to write code to test for the correct data type because it is enforced at compile time. The need for type casting and the possibility of run-time errors are reduced.                                                                                               | Generic types can be derived from most base classes, such as MarshalByRefObject (and constraints can be used to require that generic type parameters derive from base classes like MarshalByRefObject). However, .NET does not support context-bound generic types. A generic type can be derived from ContextBoundObject, but trying to create an instance of that type causes a TypeLoadException.                                                                                                                       |
| Less code and code is more easily reused. There is no need to inherit from a base type and override members. For example, the LinkedList<T> is ready for immediate use. For example, you can create a linked list of strings with the following variable declaration:                                                                                                | Enumerations cannot have generic type parameters. An enumeration can be generic only incidentally (for example, because it is nested in a generic type that is defined using Visual Basic, C#, or C++). For more information, see "Enumerations" in Common Type System.                                                                                                                                                                                                                                                    |
| Better performance. Generic collection types generally perform better for storing and manipulating value types because there is no need to box the value types.                                                                                                                                                                                                      | Lightweight dynamic methods cannot be generic.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Generic delegates enable type-safe callbacks without the need to create multiple delegate classes. For example, the Predicate<T> generic delegate allows you to create a method that implements your own search criteria for a particular type and to use your method with methods of the Array type such as Find, FindLast, and FindAll.                            | In Visual Basic, C#, and C++, a nested type that is enclosed in a generic type cannot be instantiated unless types have been assigned to the type parameters of all enclosing types. Another way of saying this is that in reflection, a nested type that is defined using these languages includes the type parameters of all its enclosing types. This allows the type parameters of enclosing types to be used in the member definitions of a nested type. For more information, see "Nested Types" in MakeGenericType. |
| Generics streamline dynamically generated code. When you use generics with dynamically generated code you do not need to generate the type. This increases the number of scenarios in which you can use lightweight dynamic methods instead of generating entire assemblies. For more information, see How to: Define and Execute Dynamic Methods and DynamicMethod. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |


## Attributes

Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).
After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called reflection.

Attributes have the following properties:
- Attributes add metadata to your program. Metadata is information about the types defined in a program.
    All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.
    You can add custom attributes to specify any additional information that is required.
- You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.
- Attributes can accept arguments in the same way as methods and properties.
- Your program can examine its own metadata or the metadata in other programs by using reflection.


## Reflections

Reflection is a feature that allows you to dynamically access, inspect, and manipulate types, members, and metadata of assemblies at runtime.
Common uses of reflections are:
- It permits the creation of new types during runtime and executes various actions utilizing those kinds.
- Attribute information can be seen during runtime.
- Late binding to functions and attributes is permitted.
- It enables instantiating and inspecting numerous kinds within an assembly.

## Threads & Tasks (TODO)

## LINQ (TODO)
