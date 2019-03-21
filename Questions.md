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
