# Learn C: Introduction

Created: February 22, 2023 6:15 AM
Status: In progress
Tags: c

---

# The C Programming Language

- C has been around for quite some time and it is one of the foundational languages of computer science.
    - C is an older language compared to other languages in use and yet it is still very popular. The [TIOBE Index](https://www.tiobe.com/tiobe-index/), which measures the popularity of programming languages, has C at the top of the list for many years. This is due to C’s use in all areas of computing.
    - Most operating systems today including the Linux Kernel are implemented with C code. The main version of the Python programming language is named CPython because it is implemented using C. C has also been extended using the languages C++ and C#.
    - C is also common in embedded systems which are smaller computing units that control things like home appliances, lighting controllers, and other small physical devices. The C programming language is everywhere.

![Hello-World-Intro.svg](Learn%20C%20Introduction%2038b46de0c3574af1a76da325044d5ea8/Hello-World-Intro.svg)

# Hello World

- So let’s look at our first C program!
    
    ```c
    #include <stdio.h>
     
    int main() {
      // output a line
      printf("Hello World!\n");
    }
    ```
    
    When this code is run the following text is displayed in the terminal.
    
    ```
    Hello World!
    ```
    
    Let’s go through the code line by line to see what is happening. You don’t need to understand everything right away, this is just a first look.
    
    - `#include <stdio.h>`: This is a preprocess-or directive in the C programming language. It tells the compiler to include the contents of the standard input/output header file (`stdio.h`) in the program before compiling it. This header file contains functions such as `printf()`, `scanf()`, `getchar()`, etc., which are used for input and output operations in C programs.
        - stdio.h ⇒ **st**andar**d** **i**nput **o**utput . **h**eader
    - `int main(){ }`: This is the main function in a C program. It is the starting point of a program and contains the code that will be executed when the program is run. The main function must return an integer value, which indicates whether the program ran successfully or not. All the code inside the curly braces `{}` runs first.
    - `// output a line`: This is a comment. It is not a line of code but a message we can add to code to tell ourselves or others what the code does. When the code is run this line will be ignored.
    - `printf("Hello World!\n");`: This line of code prints, or outputs, the text “Hello World!” to the console. Printing text to the console is one way for a program to communicate with the user. `\n` is a newline character in C.

# Syntax and Errors

When writing in C, we need to follow a set of rules in order for the code to run properly. These rules are known as *`syntax`*

## **Case Sensitivity**

**Most of the words in the code use all lowercase letters.** This is known as *`case-sensitivity.`* Whether lowercase or uppercase, certain words in the code must follow the correct case in order for the code to run. The only lines of text that can change case are the **comment** and the text between **quotes**.

## **The Semicolon**

All statements, like the `printf()` statement, need to end with a semicolon`;`. This identifies the end of the statement and is needed for the code to run correctly.

## **Double Quotes**

The text in between the double quotes `"` is known as a *`string`* (think of a string of characters). All strings must be surrounded by **double-quotes.**

So what happens when we break the rules? **The answer is *errors***. The below text is an error that is output when we leave off the semicolon from the `printf()` statement in our Hello World code.

```c
#include <stdio.h>

int Main() {
  // output a line
  printf("Hello World!\n")
}
```

```c
script.c: In function ‘main’:
script.c:6:1: error: expected ‘;’ before ‘}’ token
 }
 ^
```

The text above gives the following information:

- The component location, `In function ‘main’`
- The line and column number, `6:1`
- A description, `expected ‘;’ before ‘}’`

**Solved**:

```c
#include <stdio.h>

int main() {
  // output a line
  printf("Hello World!\n");
}
```

# Output

The main goal of our Hello World code example is to output the text `"Hello World!"`
 to the console. The line of code that outputs text is:

```c
printf("Hello World!\n");
```

Let’s dive deeper into the 2 parts of this line are:

- `printf()` is known as a function and performs the action of printing text to the console.
- `"Hello World!\n"` is a string. A string is text in between a pair of double quotes. And `\n` is a newline character. or it called an escape sequence and is used to add a non-visual character within a string.

In this case, `\n` adds a new line to the end of the string. Look what happens when we place it in between Hello and World!:

```c
printf("Hello\nWorld!");
```

**Result**

```
Hello
World!
```

It’s important to remember an escape sequence is a character and must be within the double-quotes.

Another escape sequence is `\t`. This is equivalent to the **tab** key and will insert spaces within a string:

```c
printf("Hello\tWorld!");
```

**The above code will output:**

```
Hello     World!
```

`\n` and `\t` are just two of many different escape sequences that can be put inside a string.

# Comments

When we write code it is important to document the code’s behavior. One way to do this is to add comments to our code.

Starting a line with a double forward slash, `//`, will create a comment and the entire line will be ignored when we run the code.

```c
// This is a single line comment
```

The comments like the ones above can be added above a line or block of code to describe the code’s behavior. Shorter comments can be added to the end of a line of code as well.

```c
printf("My cat is happy!"); // How my cat feels
```

In both examples, once you use `//`the rest of the line is now a comment.

If you want to create a comment with a beginning and end, you can use `/*`to begin the comment and `*/`to end the comment. This is known as a block comment:

```c
/* The following output will be
an outburst from my cat in a 
moment of pure joy after seeing 
another cat across the street. */
printf("meow!");
```

As you can see from the above example a block comment can wrap multiple lines without the use of anything but the beginning notation `/*`and the ending notation `*/`

# Compiling

While this is how most of the exercises will go it is important to learn about running your code using a compiler.

The compiler is the program that converts your code to an executable program that can be run on your computer. This involves reading the code from a file and compiling it into code the computer processor can run.

A widely used C Compiler is [gcc](https://gcc.gnu.org/), which stands for GNU Compiler Collection. Let’s look at how we can compile **`helloWorld.c`** to the **`helloWorld`** executable.

```c
// helloWorld.c
#include <stdio.h>
 
int main() {
  // output a line
  printf("Hello World!\n");
}
```

To compile this code we need to run the following command in a terminal:

```bash
gcc helloWorld.c -o helloWorld
```

The above command can be broken up into 3 pieces:

- `gcc` is how we run the compiler application.
- `helloWorld.c` is the filename of our code to be compiled.
- `-o helloWorld` is an optional but common addition to the command. It tells `gcc` to output the program executable under the name `helloWorld`. If this is left out, the executable file will be called **a.out**.

After running the command we have an executable, but how do we run our code? We can run the executable with the following command, again using the terminal:

```bash
./helloWorld
```

This command tells the computer to look in the current directory and run **`helloWorld`.**

# Summary

Let’s review what was covered:

- C has been around for a while but is still very popular
- Code syntax is a set of rules that are followed when writing code so the program is able to compile
- Errors occur when the syntax is incorrect
- Error messages make a best effort to describe the error and where it occurred
- Use `printf()` to output text to the console
- Comments are used to include text in code that the compiler will ignore
- Line comments start with `//` and block comments are surrounded by `/* */`
- The `gcc` application, or GNU Compiler Collection is a compiler used to compile C programs

---

# ***~~The End~~***