# Introduction

- [Purpose of Writing the Book](#purpose-of-writing-the-book)
- [Programming and PAWN](#programming-and-pawn)
- [The PAWN Compiler](#the-pawn-compiler)
- [Hello World](#hello-world)

## Purpose of Writing the Book
This book is written with the aim to teach the fundamental concepts of programming using one of the most beginner-friendly languages known as PAWN. Choosing PAWN as your first language can have many benefits namely familiarization with the fundamental concepts of programming, picking up good programming practices and algorithm implementing skills which are transferable to other languages. If you’re experienced in PAWN, learning a new language won’t be a difficult task for you.

Some parts of this book are written assuming that the reader is familiar with SA-MP and if you want to follow along practically, you should know the basic concepts like setting up a local SA-MP server for loading up and running scripts. There are countless resources, suggestively the official SA-MP Wiki which can teach you the process. If you want to only give a quick read to the book, it will still be beneficial for you since it will cover most of the concepts that are common in computer languages.

Observing the mainstream learning sources, I noticed a lack some fundamental sense of direction. A complete beginner can often find him or her self in a confusing and often frustrating situation where they don’t know what’s next to learn or practice, which inevitable makes half of the people quit the learning process at this point, and even if someone carries on stumbling from one guide to another, somehow managing to attain proficiency in the skill, it takes twice as long as it should. Hence, I decided to write a book, providing the reader with an organized and structured content which will pinpoint you in one direction, covering the most basic concepts to intermediate algorithm implementation, giving you the skills you need to become a developer, and in turn transfer those skills to a professional language with ease. The content in this book is the elementary and essential step towards becoming a developer, which most courses lack. This will give you a sense of direction and will teach you all the skills giving you a head start when you begin learning a professional programming language.


## Programming and PAWN
Programming is the ‘art’ of communicating with a computer and for that we use programming languages. In a natural language you use the rules of grammar to construct sentences and communicate your thoughts or implications to other people. Deviating from the rules of grammar can cause some errors in the communications. Similarly in programming, you write statements according to the rules of that programming language. These rules are generally known and referred to as ‘syntax’ of the programming language. There are many similarities between the natural and programming languages. Memorizing the whole dictionary of words might not make you proficient at a natural language but practicing to apply newly learnt knowledge does ensure that, same principal can be applied to the programming language. Practice is the universal rule of getting better and mastering any skill. 

In contrast to a programming language, Pawn is an ‘extension language’, and it cannot be used to write independent applications, rather to manipulate the resources of a host application. For-example, C# being a programming language can be used for writing powerful desktop applications, while a Pawn can be ‘installed’ in an already existing program or application like a video game, giving the ability to creatively use its resources, which might include weapons, vehicles or player models.


## The PAWN Compiler
Generally, code written in most languages is stored in the form of a special text document called ‘source file’, which contains the raw code written by the programmer. The computers cannot directly understand the raw code (often referred to as ‘source code’) in the ‘source file’. For building an executable program, the source file is converted into the executable program using a set of tools which vary depending upon the language used. 

A coding beginner does not necessarily need to know the details of program compilation, but having a rough idea of this concept does help on the long run. The PAWN compiler takes in the source file, combines it with other dependencies and creates a file with (.amx) extension which contains ‘bytecode’ also called pseudo-code (P-Code). When the program or script is required to be executed, the P-Code (.amx) file is passed into an abstract machine and executed. An abstract machine in simplest terms a virtual model of a computer system.

An ‘Integrated Development Environment’ also known as IDE in short, is a single program which contains the necessary tools for writing and compiling scripts in a language.

One of the applications in which the Pawn language has been most extensively used is the multiplayer modification of Gta San Andreas called San Andreas Multiplayer or SA-MP in short. Therefore, I decided to use the SA-MP development environment for writing the example code of this book and I expect you to follow along in the same way. The Pawn Compiler and an IDE known as ‘Pawno’ is provided along with the SA-MP server resources from the official site. If you open up the IDE which can be found in the ‘pawno’ folder in the server package, the window should look something like this :

![Pawno Editor](https://i.imgur.com/dWx12w2.png)

One neat thing about this IDE is that it’s very lightweight and almost perfect for writing PAWN code since it was specially made for this purpose. All the code in this book can be easily written and compiled using this piece of software.


## Hello World
The process of writing, compiling and running the scripts is very quick and simple which makes SA-MP development more fun. It is explained briefly in this topic, while there are countless other sources online which explain the same process in much more detail.

Navigate to the top-left corner of the IDE window and click the ‘New’ icon which will create a new script and in-turn some code will appear in the window. Delete all the code and write the follow instead :
```c
#include <a_samp>

public OnFilterScriptInit ()
{
    print ("Hello World");
    return 1;
}
```
Save the file as a filterscript and compile it using the F5 key or the ‘Compile’ icon from the toolbar. Once compiled, run the server and load the filterscript. It should show the following output in the server console :
```c
Hello World
```
This was a very simple and the traditional ‘Hello World’ program every programmer writes while learning to code. If you are following along practically, you can experiment by trying to change the output text which will make you more familiar with the code. 
