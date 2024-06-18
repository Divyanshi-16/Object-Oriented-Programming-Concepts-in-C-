# Object-Oriented-Programming-Concepts-in-C++
In this repo, we will walk through the basics of OOPs concept...

## Templates
1) Templates are a mechanism that make it possible to use one function or class to handle many different data types.
2) Template doesn't really exists until we call it.
3) template <typename T> or template <class T>
4) Compiler creates a new instance of a template function for every data type.
5) T func(T x, T y){}: datatypes of x and y should match. For instance, if datatype of x is double and that of y is int, thn it would generate a compile time error.
6) We can pass non-type arguments to templates. Non-type parameters are mainly used for specifying max or min values or any other constant value for a particular instance of template. The important thing to note about non-type parameters is, they must be const. Compiler must know the value of non-type parameters at compile time. Because compiler needs to create functions/classes for a specified non-type value at compile time.
7) Sometime we want a different behaviour of a function/class template for a particular data type. For this, we can create a specialized version for that particular data type. The specialized function or class if cdefined would only be called.
8) Example of Template Metaprogramming:-
   #include <iostream>
   using namespace std;
 
   template<int n> struct funStruct
   {
     static const int val = 2*funStruct<n-1>::val;
   };
 
   template<> struct funStruct<0>
   {
     static const int val = 1 ;
   };
 
   int main()
   {
     cout << funStruct<10>::val << endl;
     return 0;
   }
9) Templates vs Macros:-
    - The macro is expanded without any type checking.
    - The type of value returned isn't specified.
    - Bug hunting in case of macros are difficult.
10) We can inherit a new template from an existing one. For example,
    template<class T>
    class NewSample:publicSample<T>
    {
    };
11) Applications of Templates:
    - The C++ Standard Library provides many useful template classes.
    - Smart pointer classes that are of great help in avoiding memory leaks and dangling pointers.
    - Classes in iostream library that let us carry out I/O in C++.


## Exception Handling
1) The errors that occur at runtime, during execution of the program are called exceptions.
2) 3 keywords are usd- throw, catch and try.
3) Creating an object called an exception object and storing information about the exceptional condition in it.
4) Throwing the exception object using the keyword throw.
5) Throw point
6) Standard base class: exception.
7) If an exception is throw, but not caught anywhere in the program, then the program terminates abnormally.
8) If there are statements below the throw point, or remaining in the try block, they wouldn't be executed, since once an exception object is thrown, the try block expires.
9) Once the catch block has been executed, control passes to the statements below the catch block.
10) When throwing errors, the message is stored in the exception object, which is then retrieved using what().
11) try blocks can be nested. When an exception is thrown, if inner try block doesn't have a corresponding catch block, then the outer try block's catch handlers are inspected for a match. This is known as stack unwinding.
12) When an exception is thrown, th catch blocks are examined in the order in which ther are written. When it finds a match, th exception is considered handled and no further searching takes place.
13) Do not place a catch that catches a base class object before a catch that catches a derived class object. If you do, then the base class catch will catch all objects derived from that base class. As a result, derived class catch will never get executed. (Warning but will compile in case of C++)
14) catch-all block: catch( ... ){}: Compile time error will be generated if placing catch all block before any catch block. Place catch all block at the very last.
15) Advantage of exception handling are :-
- Remove error-handling code from the software’s main line of code.
- A method writer can choose to handle certain exceptions and delegate others to the caller.
- An exception that occurs in a function can be handled anywhere in the function call stack.
- Separating Error-Handling Code from “Regular” Code.
- Propagating Errors Up the Call Stack.
16) The statements which may cause problems are put in try block. Also, the statements which should not be executed after a problem occurred, are put in try block. Note that once an exception is caught, the control goes to the next line after the catch block.
17) The block catch(...) is used for catch all, when a data type of a thrown exception doesn't match with any other catch block, the code inside catch(...) is executed. Note that the implicit type conversion doesn't happen when exceptions are caught.
18) When an object is created inside a try block, destructor for the object is called before control is transferred to catch block.
19) The destructors are called in reverse order of constructors. Also, after the try block, the destructors are called only for completely constructed objects.
20) Smart Pointers prevent:-
  - Memory leaks
  - Dangling pointers
  - Deleting an object twice
  - Wrong deletion of an array
21) Unique Pointers
  - simplest smart pointers
  - scoped pointers
  - can't copy the pointers (even unique ones) (this is because copy constructors and copy assignment operator is deleted in this case)
  - unique_ptr<ClassName> cn1(new ClassName());
  - unique_ptr<ClassName> cn2=make_unique<ClassName>();
22) Shared Pointers
  - reference counting
  - when reference counting is 0, then the pointer gets deleted
  - shared_ptr<ClassName> se2=se1;
23) Weak Pointers
  - similar to shared pointers but doesn't deal with reference counting 
