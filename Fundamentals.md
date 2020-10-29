# The Pawn Language | Fundamentals

- [Comments](#comments)
- [Symbols and Operators](#symbols-and-operators)
- [String Formatting](#string-formatting)
- [Variables](#variables)
- [Constants](#constants)
- [Conditionals](#conditionals)
- [Loops](#loops)
- [Functions](#functions)
- [Enumerators](#enumerators)
- [Preprocessor Directives](#preprocessor-directives)
- [Compiler Warnings / Errors](#compiler-warnings)

Pawn is a modification of Small-C which is in-turn a subset language of the Original C. According to the Official CompuPhase definition :

> Pawn is a simple, typeless, 32-bit extension language with a C-like syntax. The Pawn compiler outputs P-code (or bytecode) that subsequently runs on an abstract machine. Execution speed, stability, simplicity and a small footprint were essential design criterions for both the language and the abstract Machine.

The concept of ‘typed’ and ‘typeless’ languages will be explained in later sections.



## Comments
The comments in a programming language are lines which are completely ignored by the compiler and hence have no effect on the program. Oddly enough, comments are one of the most useful tools in any programming language. Their importance will become more apparent as you progress in your programming career. The code from the first chapter can be reused for this example.
```c
#include <a_samp>

public OnFilterScriptInit ()
{
    // print ("Hello World");
    return 1;
}
```
If you copy-paste the above code in the IDE, compile and run it. This time it will not show anything in the console. If you have not already noticed the change in the code, it is the addition of double-slash symbols before the ‘print’ statement which basically commented out all the letters following the slashes, in that specific line. The ‘print’ statement  was responsible for ‘printing’ or showing that “Hello World” text in the server console and since it is now commented out, the compiler simply ignores that line and consequently nothing happens as the script is executed.
The preceding was an example of a single-line comment. The code in programming often exceeds hundreds and even thousands of lines and if you want to comment out a specific part of such a script, it can get quite troublesome and not-so-efficient if the single-line comments are used for that purpose. For such purposes, there is another type known as multi-line comments. The syntax for a multi-line comment is the following :
```c
/*         code, text, or anything else         */
```
A multi-line comment starts with an operator containing a forward-slash plus a star symbol (/*) and it ends with a similar operator (*/). Everything in-between is commented out. Following is a program containing multiple print statements, some of which are commented out :
```c
#include <a_samp>

public OnFilterScriptInit ()
{
    print ("This");
    print ("is");
    print ("a");

    /*
    print ("commented");
    print ("out");
    */
    
    print ("statement.");
    return 1;
}
```
##### Output:
```c
This
is
a
statement.
```
If you look at the code, there are six ‘print’ statements but four of them are executed while two are skipped, which is because those two statements are enclosed in the multi-line comment operators (/*) and (*/) and hence, commented out of the program. Multi-line comments can also be used for commenting out single lines but it won’t make much sense unless you want to comment out a specific part of that line which can be useful in some situations. Following is an arbitrary example of commenting out part of a statement (which you don’t necessarily need to understand or practice at this level) :
```c
print ( /*"Ignored"*/ "Printed" );
```
##### Output
```c
Printed
```
Other than disabling parts of code, comments can be very useful for leaving out messages in the source code for other people. Often comments are used for explaining what is the function of a specific part of the code which can help fellow programmers working on the same script, or it can be used to leave some notes or reminders for yourself in the script. Generally, it is up to you how you use them.



## Symbols and Operators
There are many symbols used in programming, each of which has a different purpose or implication. Most of them are explained in the following sub-headings.

### Basic Symbols
Before studying more about the Operators, you should know the meaning of some important symbols that do not fall in the category of Operators. These include the braces, parentheses, single quotes, double quotes and semi-colon. This will give you more familiarity with the code and in turn help you make more sense of it. Eventually you will develop the intuition and will be able to read the code easily, just like a natural language and understand the meaning.

### Braces
The basic ‘hello world’ code will be used in the following example to keep the things simple.
```c
#include <a_samp>

public OnFilterScriptInit ()
{
    print ("Hello World");
    return 1;
}
```
If you observe the code above, you will notice there are two (curly) braces used in the script. The print and the return statements appear to be ‘enclosed’ between the two braces. The first bracket is called opening-brace ({) , and the second bracket is called closing-brace (}). Everything between each such pair of braces is considered a ‘block of code’. At this point, all you need to know is that the block of code (containing ‘print’ and ‘return’) belongs to the preceding expression or statement and in this case :
```c
public OnFilterScriptInit ()
```
This relation will become more apparent as you study the properties of functions in later topics.

### Parentheses
The syntactic use of parentheses is similar to the braces but they both imply different meanings. While braces are used for enclosing a collection of statements, the parentheses are used to enclose data or others requirements that are needed by that statement. For example, the print function takes in some text input so we use the brackets to enclose that input data (the double quotation will be explained in a later section) :
```c
// A function is a keyword that performs a specific task
// In programming, a keyword is a reserved word that is recognized by a computer and has a special meaning or use.

// Empty print function, which will show an error upon compilation since it requires input :
print ();

// Syntax of a print function :
print (some text enclosed within double quotes);

// A proper print statement :
print ("Hello World");
```
*Note: A brief definition of a function is given in the preceding example but they will be covered in detail later in this chapter.*

If there is no data or arguments needed by a statement but it is of the type to accept arguments then the parentheses are still used, but left empty like in the following line : 
```c
public OnFilterScriptInit ()
```

### Semi-colon
One of the single most used operators in Pawn language is the semi-colon operator and a lot of other languages share the same property. You can think of the semi-colon (;) as a period which indicates the end of a sentence. The semi-colon operator simply indicates to the compiler about the end of a statement. For-example if you notice, in the code presented in preceding examples, the print statement(s) have a semi-colon in the end which means the it’s the end of that statement.
```c
print ("I like Pawn.");
```
It is required at the end of every single-line statement or otherwise the compiler will not be unable to distinguish between different lines of code which in-turn will show an error upon compilation.

### Single and Double Quotation Symbols
Single quotation marks, also referred to as apostrophe(s) are used to enclose a single character which indicates that the enclosed character is some data that needs to be stored somewhere or is required by a statement. This will become more clear in later topics.
While the single-quotes are used to enclose a single character, the double quotations are used to enclose a strings which basically is a term used for referring to an ‘array of characters’. Since, in programming we deal with many types of data (datatypes) which may include simple integers, decimal values, characters or a collection of characters, we classify them using specific names, and in this case the name string is used to refer to any textual form of data. 
For example, (as explained before) the print function takes in some string data and displays it in the console when the script is executed. In order to pass that data into the function, we enclose the input text between double quotation marks :
```c
// Wrong
print (Hello World);

// Correct
print ("Hello World");
```

### Revision
Now I would like you to take a look at the following code in the context of the previous explanations.
```c
#include <a_samp>

public OnFilterScriptInit ()
{
  print ("Hello World");
  return 1;
}
```
