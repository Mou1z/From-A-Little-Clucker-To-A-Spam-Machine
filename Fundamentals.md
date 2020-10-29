# The Pawn Language | Fundamentals

Pawn is a modification of Small-C which is in-turn a subset language of the Original C. According to the Official CompuPhase definition :

> Pawn is a simple, typeless, 32-bit extension language with a C-like syntax. The Pawn compiler outputs P-code (or bytecode) that subsequently runs on an abstract machine. Execution speed, stability, simplicity and a small footprint were essential design criterions for both the language and the abstract Machine.

The concept of ‘typed’ and ‘typeless’ languages will be explained in later sections.

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
#### • Braces
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
#### • Parentheses
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
#### • Semi-colon
One of the single most used operators in Pawn language is the semi-colon operator and a lot of other languages share the same property. You can think of the semi-colon (;) as a period which indicates the end of a sentence. The semi-colon operator simply indicates to the compiler about the end of a statement. For-example if you notice, in the code presented in preceding examples, the print statement(s) have a semi-colon in the end which means the it’s the end of that statement.
```c
print ("I like Pawn.");
```
It is required at the end of every single-line statement or otherwise the compiler will not be unable to distinguish between different lines of code which in-turn will show an error upon compilation.
#### • Single and Double Quotation Symbols
Single quotation marks, also referred to as apostrophe(s) are used to enclose a single character which indicates that the enclosed character is some data that needs to be stored somewhere or is required by a statement. This will become more clear in later topics.
While the single-quotes are used to enclose a single character, the double quotations are used to enclose a strings which basically is a term used for referring to an ‘array of characters’. Since, in programming we deal with many types of data (datatypes) which may include simple integers, decimal values, characters or a collection of characters, we classify them using specific names, and in this case the name string is used to refer to any textual form of data. 
For example, (as explained before) the print function takes in some string data and displays it in the console when the script is executed. In order to pass that data into the function, we enclose the input text between double quotation marks :
```c
// Wrong
print (Hello World);

// Correct
print ("Hello World");
```
#### • Revision
Now I would like you to take a look at the following code in the context of the previous explanations.
```c
#include <a_samp>

public OnFilterScriptInit ()
{
  print ("Hello World");
  return 1;
}
```
### Operators
An operator is a symbol (sometimes a combination of symbols) used in code which simply tells the compiler to perform a specific task. It behaves like a mini function.The operators used in Pawn (and some other programming languages) are divided into the following categories :
- Assignment Operators    ( = , += , -= , *= , /= ) 
- Arithmetic Operators    ( + , - , * , / , ^ )
- Relational Operators    ( < , > , == , <= , >= )
- Logical Operators       ( ! , || , &&  )
- Ternary Operator        ( condition  ?  True  :  False ; )
- Bitwise Operators       (& , | , ^, ~ , ! )

![Operators](https://i.imgur.com/pb1IKkH.png)

It’s not a small topic and since the explanations of each operator’s functioning is dependent upon the programming concepts which will be introduced (or explained) later, there I will be explaining parts of it at relevant places in later topics throughout the book. But it is important for you to be able to recognize such operators though not necessary while reading the guide as each example has been explained in detail pointing out all types of operators and symbols where necessary.
### String Formatting
The method of inserting changeable or variable data in a string is called string formatting. Formatting a string means adding ‘format specifiers’ which are symbols that are replaced by some data which may be text or values, therefore there are different format specifiers for each datatype. Till now we have been using the print function to output a string (text) in the console but there is an advanced version of it called ‘printf’. The general usage of printf function is similar to that of print but it adds the ability of formatting the input string. The syntactical difference between print and printf is the following :
```c
print (main_string);

printf (main_string, argument_1, argument_2, ...);

// print can take in only 1 argument, which is the main string
// printf takes 'atleast' one argument, followed by optional arguments that take in all types of 'data' (separated by commas).
```
The printf function takes in the first argument as the main string which may or may not contain format specifiers, while the following arguments to that (if any) contain the data that is to replace the respective format specifiers in the main string. Here is a practical example of the difference between print and printf function :
```c
print ("Your score is 100");
// Output: Your score is 100

printf ("Your score is %i", 100);
// Output: Your score is 100
```
If the above two statements are used under the OnFilterScriptInit function, both will print the same text in console when the script is loaded. In the printf statement, the main string contains a format specifier for integer data (%d). The data in first optional argument replaces the first appearing format specifier in the main string which is %d when the statement is executed during the runtime. Following is a list of format specifiers in Pawn :

![Format Specifiers](https://i.imgur.com/C1TFmeA.png)

From the above table, we know that string data uses the specifier %s. We can use that in an example :
```c
printf ("This program is written by %s in %i seconds.", "Mouiz", 10);

// Output: This program is written by Mouiz in 10 seconds.
```
The first formatting argument “Mouiz” replaces the first format specifier %s while the second one namely "10" replaces the second specifier %i. It is important to note that the format specifiers are replaced according the to order in which the formatting arguments are included, which means that if we switch the positions of ‘Mouiz’ and 10, it will show some unexpected results :
```c
printf ("This program is written by %s in %i seconds.", 10, "Mouiz");

// Output: This program is written by  in 77 seconds.
```
Which implies that the string formatting won’t work properly unless you use the correct format specifiers according to the respective arguments’ datatypes and vice versa.
Since the compiler treats certain characters in the string (like format specifiers) differently than normal letters and numbers, there are a few exceptions to the string data. The most common mistake alot of beginners make is, directly adding double quotes inside a string.
```c
printf ("The "word" is quoted"); // Wrong

printf ("The \"word\" is quoted"); // Correct
```
As the string data is already enclosed in double quotes, directly adding additional quotes inside the string is not possible, since compiler is not intelligent enough to distinguish between them. To solve this problem, there is a syntax for adding such characters in a string, which is adding a backslash \  before that character as shown above. These characters include single quotes, percentage symbols and a few others. A combination of a backslash and a character is called an Escape Sequence. An Escape Squence performs specific actions in a string like including special characters in a string (as explained above) and/or shifting the location of the cursor to prior or next line.
You might have concluded that printf just has a fancy syntax since the output is the same but there is more to it. Formatted strings are in simple words are ‘dynamic strings’. Once you compile a program using a ‘print’ statement, it will show the exact same text when the script is loaded / executed, but by using formatted strings you can make the string dynamic which is possible by passing ‘variables’ instead of data in the formatting (optional) arguments. This way, the string’s output will change depending upon the value of those variables. More on that will be explained in the next topic.



## Variables
One of the most important concepts in programming is the concept of ‘variables’. In programming, a variable is an entity that is changeable, but in terms of what ? In Pawn language, a variable holds a value at any time and that value-as the name suggests-is ‘variable’ or ‘changeable’. 
The reason why variables are so important is because they are basically small units of computer memory which can hold or ‘remember’ different values while the program is under execution (running), and that property turns out to be very useful in programming. For example, you want to keep track of the scores of 100 players in a game, you can do it easily by programming the computer to store (remember) and keep the values updated (there is an even more efficient method for storing scores called ‘Arrays’, a later topic in the book). Later if you want to find the mean score of those players or if you want to create a leaderboard, those values from the variables can be easily accessed and used.
For using a variable, first we need to declare it using a keyword plus a name for it. Following is the method of syntax of declaring a variable :
```c
// Creating (more appropriately, 'declaring') a variable named 'my_variable'

new my_variable ;

// The 'new' keyword is used for declaring a variable
// In the above line a variable is declared with the name 'my_variable'
// Semi-colon is used in the end to close the declaration statement.
```
It can be better understood by looking at some examples :
```c
new var;
new ammo;
new score;
new vehicles;
new top_score;
```
Each of the above defined variable has a value by default, which is zero. There are different ways of assigning values to a variable. One method is directly assigning a value to the variable as it’s declared :
```c
new letters = 25;
```
In the above example, a variable named ‘letters’ is being declared, with a value of 25. You will notice an equal sign which is a simple Assignment Operator that can be used for assigning values to variables. It evaluates the expression on its right and assigns the resultant value to the variable referenced on its left side. Other than assigning values directly at the declaration, you can also do it in later parts of the code :
```c
new letters;

letters = 25;
```
But this can be done only if the part of the code where you’re referencing the variable is within the scope of that variable. Scope of a variable depends upon the code block or position where that variable was declared. For example a variable being declared outside any block of code, usually in the beginning of the script, has a ‘Global’ scope and can be accessed from anywhere within the script:
```c
#include <a_samp>

new example_var = 5;

public OnFilterScriptInit ()
{
    example_var = 10;

    printf ("The value is %i", example_var);

    return 1;
}

public OnPlayerConnect (playerid)
{
    example_var = 100;
    
    printf ("The value is %i", example_var);

    return 1;
}

// Output : 
// The value is 10
// The value is 100

// Note: The second output line is shown only when a player connects.
```
In the above example, a public function (callback) has been introduced which executes the code in it’s code block only when a player connects to the server. Public Functions or more appropriately ‘Callbacks’ are functions or parts of codes that are executed by the server on specific occasions line when a player connects, shoots, moves, disconnects etc. Hence, they can be treated as ‘events’. 
Other than ‘Global’ (scoped) variables, there are ‘local’ or ‘private’ variables that can be accessed only from inside the block of code where they were declared. For-example :
```c
#include <a_samp>

public OnFilterScriptInit ()
{
    new local_var;

    local_var = 5;

    return 1;
}

public OnPlayerConnect (playerid)
{
    local_var = 10; // This line will show an error upon compilation
    
    return 1;
}
```
If you try to compile the code above, the compiler will show an error which is reasonable as a local variable is being references in a completely different block of code. 
Note: If it is a nested code block then the variable can be accessed from there.
One important thing to note is that you cannot declare variables with the same names if their scopes intercede. For example if you already have a variable named ‘score’ on a global scope, you cannot create another variable named ‘score’ on the global scope as well as a local one, and this is true for other way around as well (if you already have a local variable, avoid declaring a global variable with the same name).
```c
#include <a_samp>

new score; 

public OnFilterScriptInit ()
{
    new score = 5; // This line will show an error.
    return 1;
}
```
Now that you know how to declare variables, you need to know the naming rules for declaring variable which are listed below :
- All variable names must begin with a letter or an underscore ( _ )
- After the first initial letter, variable names can contain letters and numbers but no spaces or special characters.
- The variable names are case sensitive i.e Uppercase letters are distinct from the lowercase letters.
- Using a reserved word (keyword) as a variable name will show an error.
##### Examples:
```c
new new; // Incorrect : Using a reserved word
new _new; // Correct

new 10letters; // Incorrect : Name starting with a number
new letters10; // Correct
new letters_10; // Correct

new my name; // Incorrect : Space in the name
new my_name; // Correct

new !nternet; // Incorrect
new Internet; // Correct
```
After that, now lets look at some examples of what types of data can be stored in variable and how :
```c
new letter = 'M';


new value = 100;


new decimal_value = 1.0; 
// Works, but will show a compiler warning
// warning 213: tag mismatch


new engine_on = true; 
// Works, and will not show a compiler warning but using a Tag is suggested


new sentence = "This is a sentence"; 
// Will show an error.
// error 006: must be assigned to an array
```
A variable is capable of holding a character, integer value, boolean (true or false) and a float value (decimal value). The comments in the above code show that storing a string in a variable results into an error, the reason for which will be explained in the next chapter. Other than that, assigning a float value to a variable will result in a compiler warning, which can be avoided by adding ‘tags’. Without proper tags, the script will show warnings upon compilation but will be executable. Tags tell the compiler about the type of data that is intended to be stored in the variable, which in turn informs us in the form of errors or warning if we make a program-breaking mistake in the code. Example of tags :
```c
new decimal_value = 1.0; // Incorrect
new bool: decimal_value = 1.0 // Incorrect
new Float: decimal_value = 1.0; // Correct

new switch_on = 1.0; // Incorrect
new switch_on = true; // Incorrect, doesn't show a warning
new bool: switch_on = true; // Correct
```
Using correct tags is important to avoid any bugs or errors during program execution. 
In this chapter, the Assignment Operator, as explained before is used for assigning a value to a variable, but there are a few more operators that can be useful while dealing with variables. The ‘Arithmetic Operators’ are used for performing arithmetic operations like addition, subtraction, multiplication, division, finding the remainder and raising a value to a power.
- Addition ( + )
- Subtraction ( - )
- Multiplication ( * )
- Division ( / )
- Remainder ( % )
- Power ( ^ )
There are many applications of these operators, some of the examples are given below :
```c
// Example 1
new number = 5 + 5; // Value of 'number' is 10
```
```c
// Example 2

new val = 10 / 2; // The value of 'va' will be 5;

new val = 10 ^ 2; // The value will be 100 in this case. As 10 raised to the power 2 is 100.

new val = 4 % 2; // The stored value will be zero since the remainder when you evaluate 4 / 2 is zero.

new val = 10 - 5; // The value is 5 in this case since 5 is minused from the value 10.
```
```c
// Example 3
new a = 10; // Declaring 'a' with a value of 10
new b = 10; // Declaring 'b' with a value of 10 aswell
new c = a + b; // Assigning the sum of 'a' and 'b' to 'c'

// The above statement first evaluates everything on the right side of the Assignment Operator ( = ) and then assigns the result to whatever is on the left side.
```
```c
// Example 4
new score = 100;
score = score + 100; // Now the value of score is 200 as it adds 100 to itself, but there is a shorter method which will be explained below.
```
In the above examples, a few ways in which the arithmetic operators can be used has been demonstrated. There are some Assignment Operators which are specifically called ‘Compound Assignment Operators’, in which the base assignment operator is combined with an arithmetic symbol to form a new operator which can be useful in assigning values to the variables. These include += , -= , *=, /= and a few others which are not very frequently used.
```c
new num = 100;

num += 100; // Adds 100 to 'num'

num -= 199; // Subtracts 199 from 'num'

num *= 2; // Multiplies 'num' by 2

num /= 2; // Divides 'num' by 2

// Final value of 'num': 1
```
