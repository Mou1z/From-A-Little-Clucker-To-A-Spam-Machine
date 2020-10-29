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
#### Output:
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
#### Output
```c
Printed
```
Other than disabling parts of code, comments can be very useful for leaving out messages in the source code for other people. Often comments are used for explaining what is the function of a specific part of the code which can help fellow programmers working on the same script, or it can be used to leave some notes or reminders for yourself in the script. Generally, it is up to you how you use them.
