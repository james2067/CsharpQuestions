##    Q: What is a namespace?
Namespaces are used primarily in two ways.

**Organizing classes**

Look at the code: `System.Console.WriteLine("Hello world");`

System is the namespace. Console is the class inside of that namespace.

You can use the "using" keyword at the top of your program to eliminate some repetition here.

For Ex: `Using System;`

Now you can use: `Console.WriteLine("Hello World");`

**Custom namespaces**

You can create your own namespaces to use throughout larger projects.

For Ex:
```
namespace ExampleNamespace
{
    class ExampleClass
    {
        public void ExampleMethod()
        {
            System.Console.WriteLine(
              "ExampleMethod inside ExampleNamespace");
        }
    }
}
```

Doing this will help you control the scope of your classes, and the names of your methods throughout your program.

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/namespaces/

##    Q: What are value types?

**Main Feature of Value Types**

In c# value types are "types" that hold a specific "value".

*Note:* Value types cannot be set to null by default.

**List of Common Value Types**
* bool
* char
* double
* float
* Int
* struct

**How to Initialize**

You could have a type "int" hold the value of "10".

`int name = 10;`

or if you wanted to user to input the value of "name" you could write this.

`int name = Console.ReadLine();`

or if you want to initialize the "type" to its default value you can use the `new` operator.

`int name = new int();`
* you can find a list of default values [here](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/default-values-table)

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/value-types

##    Q: What are reference types?

Reference types are different from value types because a reference type does not hold the "value". Instead it holds a pointer to location in memory where that "value" is stored.

**List of Reference Types**
* String
* Class
* Delegates
* All arrays, even if their elements are "Value Types"

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/reference-types

##    Q: What is an automatic property and how is it useful?

An automatic property is created by the compiler. Which automatically creates a private field and populates the get and set method with the basic code required to read and write the field.

*Why is it useful?*

Allows us to shorten the syntax required for declaring public properties for private fields.

**Syntax Example**

`public string Name { get; set; }`

https://csharp.net-tutorials.com/csharp-3.0/automatic-properties/

##    Q: What is the purpose of using statement?

Provides a convenient syntax that ensures the correct use of IDisposable objects.

When the lifetime of an IDisposable object is limited to a single method, you should declare and instantiate it in the using statement. The using statement ensures that Dispose is called even if an exception occurs within the using block.

Within the using block, the object is read-only and cannot be modified or reassigned.

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-statement

##    Q: What are dynamic type variables?

A dynamic type escapes type checking at compile time; instead, it resolves type at run time. 

Ex: `dynamic nameHere = 1;`

At compile time this would be read as `object nameHere = 1;` but at runtime the "dynamic" type resolves to `int nameHere =1;`

*Note:* A dynamic type changes its type at runtime based on the value of the expression to the right of the "=" operator.

https://www.tutorialsteacher.com/csharp/csharp-dynamic-type

##    Q: What is the purpose of the is operator?
##    Q: What are generics and how is using them useful?
##    Q: What is the scope of a public member of a class?
##    Q: Can you create a function that can accept a varying number of arguments?
##    Q: How do you sort an array?
##    Q: What is a nullable type and what purpose does it serve?
##    Q: What is an enumeration?
##    Q: What is inheritance?
##    Q: Is multiple inheritance supported?
##    Q: What is the purpose of as operator
##    Q: What is an object?
##    Q: What is the difference between a struct and a class?
##    Q: What is the difference between continue and break statements?
##    Q: What is this and how is it used?
##    Q: What is try and catch and when are they used?
##    Q: How is exception handling done?
##    Q: What is finally and what is its purpose?
##    Q: List the differences between Array and ArrayList.
##    Q: What is an object?
##    Q: Define constructor.
##    Q: When can var be used to declare a variable and how is the type for the variable determined?
##    Q: What is an abstract class?
##    Q: What is an interface?
##    Q: What is a method?
##    Q: What is a property?
##    Q: What is an access specifier?
##    Q: What access specifiers are supported and what do they mean?
##    Q: What is a collection?
##    Q: What is a Hash Table?
