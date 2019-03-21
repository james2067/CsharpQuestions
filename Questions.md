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

**Main Purpose**

The is keyword evaluates type compatibility at runtime. It determines whether an object instance or the result of an expression can be converted to a specified type.

**Synstax Ex:**

```
if (obj is Person) {
   // Do something if obj is a Person.
}
```

The `is` statement is true if:
* obj is an instance of the same type as Person
* obj is an instance of a type that derives from Person. 
* obj has a compile-time type that is a base class of Person.
* obj is an instance of a type that implements the Person interface.

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/is

##    Q: What are generics and how is using them useful?

**Main Purpose**

Generics allow you to define a class with placeholders for the type of its fields, methods, parameters, etc. Generics replace these placeholders with some specific type at compile time.

A generic class can be defined using a pair of angle brackets like so.

`class MyGenericClass<T>`

Here MyGenericClass is defined with <T>. <> indicates that MyGenericClass is "generic" and its underlying type will be defined later on. For now we consider its type to be "T".

https://www.tutorialsteacher.com/csharp/csharp-generics

##    Q: What is the scope of a public member of a class?

There are a few different access modifiers that c# uses. Public is one of them.

A Public access modifier can be accessed by any other code in the same assembly or another assembly that references it.

Public access is the most permissive access level. There are no restrictions on accessing public members.

**Syntax Ex:**
```
class PointTest
{
    public int x; 
    public int y;
}

class MainClass4
{
    static void Main() 
    {
        PointTest p = new PointTest();
        // Direct access to public members:
        p.x = 10;
        p.y = 15;
        Console.WriteLine("x = {0}, y = {1}", p.x, p.y); 
    }
}
// Output: x = 10, y = 15
```

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public

##    Q: Can you create a function that can accept a varying number of arguments?

**Yes!**

In c# this can be done very easily by using the `params` keyword.

By using the params keyword, you can specify a method parameter that takes a variable number of arguments.

**Syntax Ex:**
```
void PrintReport(string header, params int[] numbers)
{
    Console.WriteLine(header);
    foreach (int number in numbers)
        Console.WriteLine(number);
}
```

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/params

##    Q: How do you sort an array?

Sorting arrays in c# can be done many ways due to the fact you could be sorting them along side a number of things.

If you wanted to sort a one-dimensional array it could be done using this syntax:

`public static void Sort (Array nameofArray);`

Sorting this way uses the IComparable implementation of each element inside the array.

*Exceptions:*
* If the array is null
* If the array is multidimensional *(note) you can sort multidimensional arrays, but it must be done differently*
* If one or more of the array elements do not implement the IComparable interface.

https://docs.microsoft.com/en-us/dotnet/api/system.array.sort?view=netframework-4.7.2#System_Array_Sort_System_Array_

##    Q: What is a nullable type and what purpose does it serve?

As mentioned previously you cannot assign a value type to null.

However you can use a nullable type to assign null to value type variables. You can declare nullable types using `nullable<t>` where t is a type.

**Syntax Ex:**

`Nullable<int> i = null;`

**What purpose does it serve?**

If you are allowed to pass a value as null, then you can more easily error check it in the future. 

https://www.tutorialsteacher.com/csharp/csharp-nullable-types

##    Q: What is an enumeration?

An enumeration is a set of named integer *constants*. 

An enumerated type is declared using the `enum` keyword.

**Syntax Ex:**
```
enum <enum_name> {
   enumeration list 
};
```
* enum_name specifies the enumeration type name. (like "Month")
* enumeration list will be a comma seperated list of identifiers. (like like the months of a year)

https://www.tutorialspoint.com/csharp/csharp_enums.htm

##    Q: What is inheritance?

Inheritance is a feature of object-oriented programming languages that allows you to define a base class that provides specific functionality (data and behavior) and to define derived classes that either inherit or override that functionality.

Basically this allows your classes to inherit the members of a parent class, and the inheritance is transitive. So even though your classes can only inherit from one other class. If class D inherits from class C which inherits from class B then class D will also have access to the members of class B.

https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/inheritance

##    Q: Is multiple inheritance supported?

**NO!**

As mentioned in the previous question. A class can only inherit from one other class. 

However inheritance is transitive. 

https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/inheritance

##    Q: What is the purpose of as operator

**Main Purpose**

In c# the `as` operator is used to perform certain types of conversions between compatible reference types or nullable types.

**Syntax Ex:**
```
class ClassA { }
class ClassB { }

class MainClass
{
    static void Main()
    {
        object[] objArray = new object[6];
        objArray[0] = new ClassA();
        objArray[1] = new ClassB();
        objArray[2] = "hello";
        objArray[3] = 123;
        objArray[4] = 123.4;
        objArray[5] = null;

        for (int i = 0; i < objArray.Length; ++i)
        {
            string s = objArray[i] as string;
            Console.Write("{0}:", i);
            if (s != null)
            {
                Console.WriteLine("'" + s + "'");
            }
            else
            {
                Console.WriteLine("not a string");
            }
        }
    }
}
/*
Output:
0:not a string
1:not a string
2:'hello'
3:not a string
4:not a string
5:not a string
*/
```

This syntax shows the `as` operator comparing each element of the array to a string. If the element is a string it prints out the contents of said string. You can tell it worked because only the 3rd element is printed.

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/as

##    Q: What is an object?

An object is basically a block of memory that has been allocated and configured according to the blueprint.

C# is an object-oriented language, thus you can expect to be using many objects throughout your program.

**Syntax Ex:**
```
public struct Person
{
    public string Name;
    public int Age;
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}

public class Application
{
    static void Main()
    {
        // Create  struct instance and initialize by using "new".
        // Memory is allocated on thread stack.
        Person p1 = new Person("Alex", 9);
        Console.WriteLine("p1 Name = {0} Age = {1}", p1.Name, p1.Age);

        // Create  new struct object. Note that  struct can be initialized
        // without using "new".
        Person p2 = p1;

        // Assign values to p2 members.
        p2.Name = "Spencer";
        p2.Age = 7;
        Console.WriteLine("p2 Name = {0} Age = {1}", p2.Name, p2.Age);

        // p1 values remain unchanged because p2 is  copy.
        Console.WriteLine("p1 Name = {0} Age = {1}", p1.Name, p1.Age);

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/*
  Output:
    p1 Name = Alex Age = 9
    p2 Name = Spencer Age = 7
    p1 Name = Alex Age = 9
*/
```

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/objects

##    Q: What is the difference between a struct and a class?

A class or struct declaration is like a blueprint that is used to create instances or objects at run time.

If you define a class or struct called `Person`, `Person` is the name of the type. If you declare and initialize a variable `p` of type `Person`, `p` is said to be an object or instance of `Person`. Multiple instances of the same `Person` type can be created, and each instance can have different values in its properties and fields.

**Struct**

A struct is a value type. 

When a struct is created, the variable to which the struct is assigned holds the struct's actual data. 

When the struct is assigned to a new variable, it is copied. The new variable and the original variable therefore contain two separate copies of the same data. Changes made to one copy do not affect the other copy.

Structs are best suited for small data structures that contain primarily data that is not intended to be modified after the struct is created.

**Class**

A class is a reference type. 

When an object of the class is created, the variable to which the object is assigned holds only a reference to that memory. 

When the object reference is assigned to a new variable, the new variable refers to the original object. Changes made through one variable are reflected in the other variable because they both refer to the same data.

In general, classes are used to model more complex behavior, or data that is intended to be modified after a class object is created. 

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/

##    Q: What is the difference between continue and break statements?

**Continue**

The continue statement causes the loop to skip the remainder of its body and immediately retest its condition prior to reiterating.

```
using System;
namespace Demo {
   class Program {
      static void Main(string[] args) {
		
         /* local variable definition */
         int a = 10;
         
         /*  loop execution */
         while (a > 20) {
            if (a == 15) {
               /* skip the iteration */
               a = a + 1;
               continue;
            }
            Console.WriteLine("value of a: {0}", a);
            a++;
         } 
         Console.ReadLine();
      }
   }
}
```

**Break**

The break statement terminates the loop and transfers execution to the statement immediately following the loop.

```
using System;
namespace Demo {
   class Program {
      static void Main(string[] args) {
         /* local variable definition */
         int a = 10;
         
         /* while loop execution */
         while (a < 20) {
            Console.WriteLine("value of a: {0}", a);
            a++;
            
            if (a > 15) {
               /* terminate the loop using break statement */
               break;
            }
         }
         Console.ReadLine();
      }
   }
}
```

https://www.tutorialspoint.com/What-is-the-difference-between-break-and-continue-statements-in-Chash

##    Q: What is this and how is it used?

**Main Purpose**

The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.

Basically, you can use it to access private instances of classes and use them with public objects.

**Syntax Ex:**
```
class Employee
{
    private string name;
    private string alias;
    private decimal salary = 3000.00m;

    // Constructor:
    public Employee(string name, string alias)
    {
        // Use this to qualify the fields, name and alias:
        this.name = name;
        this.alias = alias;
    }

    // Printing method:
    public void printEmployee()
    {
        Console.WriteLine("Name: {0}\nAlias: {1}", name, alias);
        // Passing the object to the CalcTax method by using this:
        Console.WriteLine("Taxes: {0:C}", Tax.CalcTax(this));
    }
```

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/this

##    Q: What is try and catch and when are they used?

The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.

The `try` block contains the guarded code that may cause an exception.
```
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```
If the `try` block causes an exception then the program will move to the appropriate `catch` block. For example if you are trying to cast a null object you will raise the NullReferenceException. In this case you could have a `catch` block similar to the following:
```
catch (InvalidCastException e)
{
}
```

This will allow you to have custom error messages based on the error the program recieves.

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch

##    Q: How is exception handling done?

Exception handling is done by using `try-catch` statements or `try-catch-finally` statements.

For more information on `try-catch` statements look at the previous question.

In a `try-catch-finally` statement the only difference is that the `finally` block will be ran no matter what exception is thrown in the `try` block.

##    Q: What is finally and what is its purpose?

As mentioned above, `finally` is an optional ending to a `try-catch` statement. 

The `finally` block is the section of code that is ran nomatter what exceptions are thrown in the `try` block.

##    Q: List the differences between Array and ArrayList.

**Array**

* Strongly typed. An array can only store one specific type of elements.
* Upon initialization an arrays size is fixed.
* Items of an Array dont need to be cast when retrieving them because Arrays are strongly typed.

**ArrayList**

* Can store any type of elements.
* grows automatically, and you do not need to specify size.
* Items of an ArrayList must be cast to appropriate data types while retrieving. 

https://www.tutorialsteacher.com/articles/difference-between-array-and-arraylist-in-csharp

##    Q: Define constructor.

When a class or struct is created, its constructor is called. 

It is used to assign initial values to the data members of the same class.

**Syntax Ex:**
```
class Geek
{   
  .......
  // Constructor
  public Geek() {}
  .......
}

// an object is created of Geek class,
// So above constructor is called
Geek obj = new Geek(); 
```

https://www.geeksforgeeks.org/c-sharp-constructors/

##    Q: When can var be used to declare a variable and how is the type for the variable determined?

`var` is an implicit type.

This means that the compilier will determine the type itself, and it is just as strongly typed as if you had declared the type yourself.

**Ex:**
You write `var i = 10;`
The compiler will read `int i = 10;`

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/var

##    Q: What is an abstract class?

**Abstraction**

The abstraction modifier can be used with classes, methods, properties, indexers, and events.

It is used to indicate that there are missing or incomplete implementations.

**Abstract Classes**

Use the abstract modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.

This allows for much neater code.

Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/abstract

##    Q: What is an interface?

An interface contains definitions for a group of related functionalities that a class or a struct can implement.

By using interfaces, you can, for example, include behavior from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes.

In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.

**Properties**
* An interface is like an abstract base class with only abstract members. Any class or struct that implements the interface must implement all its members.
* An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.
Interfaces can contain events, indexers, methods, and properties.
* Interfaces can contain events, indexers, methods, and properties.
* Interfaces contain no implementation of methods. **IMPORTANT**
* A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/interfaces/

##    Q: What is a method?

A method is a code block that contains a series of statements. A program causes the statements to be executed by calling the method and specifying any required method arguments.

In C a method would be called a function.

Methods are great for shortening your code. 

**Syntax Ex:**
```
class TestMotorcycle : Motorcycle
{

    public override double GetTopSpeed()
    {
        return 108.4;
    }

    static void Main()
    {
        
        TestMotorcycle moto = new TestMotorcycle();

        moto.StartEngine();
        moto.AddGas(15);
        moto.Drive(5, 20);
        double speed = moto.GetTopSpeed();
        Console.WriteLine("My top speed is {0}", speed);            
    }
}
```

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods

##    Q: What is a property?

**Definition**

A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.

**Overview**

* Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.
* A get property accessor is used to return the property value, and a set property accessor is used to assign a new value. These accessors can have different access levels. For more information, see Restricting Accessor Accessibility.
* The value keyword is used to define the value being assigned by the set accessor.
* Properties can be read-write (they have both a get and a set accessor), read-only (they have a get accessor but no set accessor), or write-only (they have a set accessor, but no get accessor). Write-only properties are rare and are most commonly used to restrict access to sensitive data.
* Simple properties that require no custom accessor code can be implemented either as expression body definitions or as auto-implemented properties.

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties

##    Q: What is an access specifier?

All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers

##    Q: What access specifiers are supported and what do they mean?

* Public
	* Can be accessed by any other code in same assembly or another assembly that references it.
* Private
	* Can be accessed only by code in the same class or struct.
* Protected
	* Can be accessed only by code in the same class, or in a class that is derived from that class.
* Internal
	* Can be accessed by any code in the same assembly, but not from another assembly.
* Protected Internal
	* Can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.
* Private Protected
	* Can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers

##    Q: What is a collection?

Collections are another way of creating and managing groups of related objects.

They provide a flexible way to work with groups of objects. Unlike arrays, the group of objects you work with can shrink and grow dynamically as the needs of the application change. 

A collection is a class, so you must declare an instance of the class before you can add elements to that collection.

**Syntax Ex:**
```
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections

##    Q: What is a Hash Table?

Represents a collection of key/value pairs that are organized based on the hash code of the key.

There are many different properties and methods that are usable from the `hashtable` class. [here](https://www.tutorialspoint.com/csharp/csharp_hashtable.htm)

**Syntax Ex:**
```
using System;
using System.Collections;

namespace CollectionsApplication {
   class Program {
      static void Main(string[] args) {
         Hashtable ht = new Hashtable();
         
         ht.Add("001", "Zara Ali");
         ht.Add("002", "Abida Rehman");
         ht.Add("003", "Joe Holzner");
         ht.Add("004", "Mausam Benazir Nur");
         ht.Add("005", "M. Amlan");
         ht.Add("006", "M. Arif");
         ht.Add("007", "Ritesh Saikia");
         
         if (ht.ContainsValue("Nuha Ali")) {
            Console.WriteLine("This student name is already in the list");
         } else {
            ht.Add("008", "Nuha Ali");
         }
         
         // Get a collection of the keys.
         ICollection key = ht.Keys;
         
         foreach (string k in key) {
            Console.WriteLine(k + ": " + ht[k]);
         }
         Console.ReadKey();
      }
   }
}
```
