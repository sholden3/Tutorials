# Intro

So far we have gone over the basics of Computer Science, C and program development, and how to build our program. At this point, we want to actually start diving into the actual building blocks of a program.

## Comments and Documentation

Though I know that you want to start coding, and I don't blame you. At this point we largely just talked about the theoreticals behind the code. But before you actually start programming, we want to talk about comments and documentation.

This is an extremely important topic, and there are whole books and frameworks and libraries that revolve around them.

But to get back to it, when we write our programs we need to keep in mind the readability of our program. There are many ways for you to do this, and we aren't aiming to go over each one of these. This is because these can be dependent on the established standards of where you work, or personal preferences.

Instead, we want to look at making sure you understand the basics prinicples of why we do it. As well as this, we want to beat into your head that you should always keep this in mind when creating your programs.

So we are going to use comments in our program with the direct purpose of both documenting our code, and maintianing readability of your code. We do this because it helps us maintain our code for the long run. It allows us to remind ourselves, as well as others reading our code, what our code actually does. Or atleast, what it is suppose to do.

You comments should also be human readable. You comments will not be included in your code at compile time. It is just there for you. This means that your code does not have to follow a syntax. This also means that your code should be understandable for everyone, including people who didn't write the code itself. It shouldn't be vague, or contain information or shortforms for words that only you understand.

So this is a pretty simple definition, but let's break down really why we want to make use of comments in our code. To do this, I want to break it down into two major reasons:

*   Comments are very useful to understand a program that you are returning to. You shouldn't be exptected to, nor will you, be able to remember each and every function or line of code that you have written. After months, or even years, after writing a program, you still want to remember what it does.
    *   I was once tasked with creating a cloud based web application for a bunch of users to upload and view data straight into BigQuery. Due to a tight deadline I did not properly document my code. The code base for this project ended up growing in size to several thousand lines of javascript code. Eventually I finished the project and shelved the code. Over a year later, I received a request to move the code to be based on an angular electron app. When rebuilding the code, I couldn't remember what half of the more obscure functions I built even did. I couldn't remember what belong to what and which functions I could safely remove as potentially redundant.
*   The previous point builds into the next, which is that even one simple comment can save you a significant amount of time trying to re-understand the code you wrote.
    *   When trying to explain my code in a meeting, a simple comment can save you from humiliation. Nothing is worse than someone who is well-versed in the language you are writing in calling you out on a function that you don't even remember what it did. A simple comment can help you defend your design decisions by refreshing you on why you made that specific decision.

So now you should see why comments are important. The next question is how we should actually use the comments. There are two different syntax's for your comments in C that you can use. In the first way, we can use the / character and the * character. These mark the beginning of our comment. We also terminate the comments as well be ending them with the character * and /. These are called multi-line comments. So all characters between the opening /* and closing */ are treated as part of the comment itself.

The other form that a comment can take is by using two consecutive slash characters //. Any characters that follow these slashes up to the end of the line are ignored by the compiler. We call these single line comments.

Now let's go ahead and give some examples of comments:

```c
/*
 * This is a multi-line comment.
 * Everything between the slashes is commented out.
*/

/*******************************
 * Here we make our comment stand out.
 * We can even add astericks within this comment for extra styling *
*******************************/

// This is a single line comment on its own line. The below is a function call.
printf("Comment Show Off"); // We can even add comments after a statement.
```

This should give you some type of an idea of how to use comments, but let's look at a more useful example. How would we actually use this in a program? As a quick side note, there are many different style guides for C. I would suggest googling for them and sticking to one for now. When you start working there will probably be a company or group specific guide for you to follow yourself.

```c
/*
 * Author: Wes Holden
 * Purpose: This program takes the sum of two variables
 * Date: 04/22/2022
*/

#include <stdio.h>

int main(void) 
{
    // Declare our three variables
    int firstValue;
    int secondValue;
    int sumOfBoth;

    // Assign the values to our three variables
    firstValue = 100;
    secondValue = 50;
    thirdValue = 100 + 50;

    // Display the result of our calculations
    printf("The sum of %i and %i is %i\n", firstValue, secondValue, sumOfBoth);

    return 0;
}
```

As you can see, even if you don't know the code for this program, you can quickly scan the comments and get a rough idea of what each group of code is doing. This makes the program much more readable.

One thing to keep in mind is that there is such a thing as too many comments. You comments should be simple and straight to the point. By adding too many comments or comments that are overly complex you risk actually complicating your code or misinforming your readers. So keep in mind that you should be using comments intelligently. Put yourself in the mindset that whoever is reading your code has no idea how to code. Your more complex analysis of your code can be saved for the documentation itself.

Now, when you are writing your code, it is a good habit to create comments as you program, not after you are done. There is nothing wrong with altering a comment after you have written it if the fundamental purpose of the comment has changed. This allows you to create comments while the program logic is fresh in your mind. This also helps with any logic errors when you are debugging. This idea of commenting as you write will be even more evident when we get into test-driven development later on in our courses.

Another aspect of commenting is something that is called self documenting code. By using meaningful names in your code, you can actually go without creating a comment. An example of this is below:

```c
/*
 * Not meaningful
*/

int a = 50;
int b = 50;
int c = a + b;
```

Though this is a pretty simple example that you can get the gist of from just looking at it, you can see where the issues might arise. What does a and b stand for? Why are we adding them? Let's look at an example of self documenting code:

```c
/*
 * Meaningful
*/

int graduatingSeniors = 50;
int nonGraduatingSeniors = 50;
int classOf2020 = graduatingSeniors + nonGraduatingSeniors;
```

Though the names are much longer, they tell a story that you can understand just be reading the variable names. This allows you to understand the purpose of code without having to add a comment.

Another aspect of code commenting is commenting  our functions themselves. This is an art in of itself, and you will get your own style for it. This is a good format to use though:

```c
/*
 * Function: Name of Function
 * --------------------------
 * Definition of what the function does. Can be multiple lines.
 * 
 * n: the argument for the function. If multiple arguments, list all of them
 * here on multiple lines.
 * 
 * returns: What we are expecting the function to return.
 * Can be multiple lines as well
*/
```

This is really all you need to know for comments here. Different languages have different ways for you to comment your code. As well as this, some languages and IDE's may have additional functionality. For C#, you can make use of xml to create comments and documentation. In Python, there are class a function comments you can create that will actually create your documentation for you as well.

# Preprocessor

One thing you might have noticed in our above code, and even the code from before that we have written, is that we make use of:

```c
#include
```

In C, we call this a preprocessor. Now we will go in more detail over preprocessors later on, but let's go ahead and look at it at a high level, to get our feet wet.

The preprocessor itself is a unique feature that can be found in both C and C++. It isn't really found in other high-level programming languages. At least none that I know of. The ultimate goal of the preprocessor is to make our programs easier to develop, read, modify, and port to other systems. It is a pretty powerful tool for us to learn, and that is why it is so very important for us to understand event at the most shallow level what is going on.

The preprocessor is tied to our C compilation process. On top of this, the compiler recognizes all of our preprocessor statements as special statements. It will analyze these statements before it analyzes the c program itself. So we can view the preprocessor at an instruction to the compiler itself, telling it to do an particular action before compiling our source code. It helps to remember this is by breaking down the word preprocessor. We can separate this into two words, Pre and Process. This shows that we need to take a certain action BEFORE we PROCESS the rest of the code. Now, we typically have the preprocessor at the top of our code, but we can actually have it anywhere in our code. The compiler will find these and act on them before we actually compile the source code.

Preprocessor commands, or statements, are identified in our code through the # sign. These have to be the first non-space character on that line. If you remember from our first program we wrote, #include is a preprocessor statement. We call this the #include directive. Now we will break down the #include directive in the next section, but it is used so often I find it helpful to bring it up really quick.

But the preprocessor isn't just limited to the #include directive. Though this is a very essential directive, there are other directives and uses for the preprocessor:

* We use the preprocessor to create our own constants and macros by using the #define statement. You will see this a lot when we do game programming in Unreal if you are interested in game programming.
* We use it to build our own library files with the #include directive that you already saw. We aren't just limited to using libraries that already come with our compiler.
* We can extend the utility of our program through the use of conditionals such as #ifdef, #endif, #else, and #ifndef statements.

We will be going over all of these later in the course. But to wrap everything up, all of these preprocessor directives will help with the efficiency of our code, and run before our code is compiled.

# #include Directive

Now, as was mentioned above, the #include directive is a very important part of any of our C programs that we will be writing in the future. It was the first statement that we ever wrote in our code, and outside of the top level file comment, will typically be the first line of code you write for every program you create. So, seeing as it is so important, let's discuss it in a little more detail.

Go ahead and create a folder on your computer, and call is CProgramming, and inside of it create a folder called examples. In reality you can name it anything you want, but we are going to keep some files in there for our examples.

So let us go and create our folders:

```cmd
mkdir CProgramming
cd CProgramming
mkdir Examples
cd Examples
```

Now I am going to create my project. You can name yours anything you want to. I will also be creating a basic folder setup as well for it:

```cmd
mkdir Example1
cd Example1
mkdir src
mkdir obj
mkdir bin
type nul > src/main.c
code src/main.c
```

Now we can go ahead and create our program:

main.c
```c
/*
 * Author: Wes Holden
 * Purpose: Discuss the purpose of preprocessors
 * Date: 03/25/2023
*/

#include <stdio.h>

int main(void) 
{
 printf("Please Work");
 return 0;
}
```

Let us go ahead and run this:

```cmd
gcc src/main.c -o bin/main.exe
```

Now from what we have learned, because it starts with a # character, our #include statement is a preprocessor directive. But what is this actually doing? If you know another language, in particular one with an import statement, this is the samething. One thing to keep in mind is that the #include #preprocessor directive is not necessary for our program. But if we aren't imporing in a library, we are greatly hindered in what we are able to do within our program. For our program above, we need the <stdio.h> library to import in our printf function. Without it, we would have an error in our code as our compiler won't know what the printf function does as it is not defined. But let's breakdown exactly what our #include statement is doing:

*   When we run the code, our compiler will see our #include directive, and will be instructued to INCLUDE in our program the contents of the file stdio.h.
    *   This is called a header file because we typically will include it at the head of our program source file.
    *   We can further denote this as a header file through the .h extension. This isn't a C file as C files are followed by a .c extension.

So now we have a basic understanding of what our #include directive is doing, but now we have the topic of a header file that we want to look at. So let us see what this is exactly:

*   A header files purpose is to define information about some of the functions that are provided by the header file itself.
    *   We know that the stdio.h is a standard C library header and provides us with the functionality for displaying output, alongside many other useful functions.
    *   We need to include this file in our program to have access to the printf() function.
    *   Within the stdio.h file lives the information that the compiler will need to understand what the printf() function is.

So, to wrap up the above, the header file is used to specify any information that the compiler will need to integrate these predefined functions inside of our program. There are many other header files out there outside of stdio.h. We previously talked about a few of these, but there are many more. In addition to these, we will also be creating our own in this course. This will allow us to reuse core features of our program in with other programs. It isn't sensible for us to have to rewrite the same processes or even similar processes inbetween different programs we use.

For the syntax of your header file, this will depend on the system you are on. Some systems, the header file names are case sensitive, while others they aren't. To be safe, you should always write the name of your header files in lowercase.

There are two ways to #include your header files in a program:

*   Angle brackets (#include <stdio.h>)
    *   This will tell the preprocessor to look for the file in one or more standard system directories. This is usually reserved for your standard libraries.
*   Double quotes (#include "mylibrary.h")
    *   This tells the preprocessor to first look in your current directory. We will use this mainly when referencing header files we created or non standard library header files.

Every C compiler that conforms to the newest standard of C will always have a set of standard header files supplied with it. This makes our lives as programmers, especially entry level learners, much easier.

You will also learn how to protect yourself from accidently including multiple instances of a header file in your program through the use of #ifndef and #define. This is mostly for efficiency. So let's break this down with a simple example of a header file:

```c
// typedefs
typedef struct region_st regions;

// function prototypes
void get_regions(regions *);
void show_regions(const regions *);
char * s_gets(char * st, int n);
```

So we see from the above simple example that a header file can include many different things. It can include #define directives, structure declarations, typedef statements, and fucntion prototypes. Though we won't get into these things here, it can be very helpful to know what you will be adding you your code when you use #include.

One last thing on header files that we will bring up is that executable code typically goes into our source code file, not the header file. There are some exceptions to this, but we won't typically do this. We will typically just have the definitions in our header file for linking purposes to tell our compiler that these functions exist.

Now we will be diving more into header files soon once we touch on having multiple files in our C program. Some may think that it is better to have the discussion on large scale projects for later, but by tackling it sooner than later we can make sure that you are prepared to efficiently write your programs, and not rely on having everything in one file.

# Displaying Output

So at this point we have talked about what a directive is, now let us go ahead and talk about how we are using this directive to actually display data.

As you might have noticed, especially seeing that we have mentioned it several times at this point, we use printf() as our function to display our output. But what exactly is the prinf() function?

*   printf() is a standard library function that we import in when we use the #include directive with the <stdio.h> header file.
    *   It outputs information to the command line or whatever you have your standard output stream set to.
    *   The information that is displayed when you use printf() is based on the arguments that you pass into it. printf("Test"); will display Test because I passed the string literal into it as an argument.
    *   Like other statements, we end this one with a semicolon as well.
*   Typically the most common function you will use in C. This is because displaying output is such an essential functionality that you will need while debugging and checking to see if your output matches what you expect it to.
*   Building ontop of this, printf() provides an easy and very convenient way to display any results of your program. This doesn't necessarily mean the output, but if you want to keep track of a series of steps and or calculations, you can use printf(). Like I said, this ties into the idea of debugging.

Overall the basic idea of displaying output, as well as printf(), is pretty simple. We will be coming back to this many times in the future, but there is another topic we need to talk about that ties intimately into displaying output.

# Reading Input

Another very valuable topic and concept that is important for us to start to get a grasp of is the use of inputs. Though we might not have down all of the concepts to utilize this fully, much like the preprocessor you are doing nothing but helping yourself by familarizing yourself with this.

By allowing us to accept inputs from an user, we are able to greatly expand what out program is capable of. Imagine all of the applications you use. Think of all of the ones that directly interact with you. Using a software like Tableau, you are able to use inputs to create dynamic and powerful visualizations. Now, imagine if everything that you use was hard coded without the capability of interacting with you as a user. For us though we will use the terminal or console to ask and take in inputs. This might not be as fancy as a GUI, but it is still very powerful.

The C library itself contains several input functions that we can use, but the most common and easiest to use for us will by the scanf() function. The scanf() function has the ability to read in a variety of formats from the user.

Let's break down what scanf() does though so that we get a good idea of what it does:

*   Scanf() reads the input from the standard input stream, or stdin, and will then scan that input according to the format that we will provide for it.
    *   These formats can be a simple constant string, but we aren't limited to just this:
        *   %s is used to read a string.
        *   %d is used to read an integer.
        *   %c is used to read a character.
        *   %f is used to read a float.
*   When using the keyboard to enter in your input into the stdin, the keyboard will actually convert your key presses and the related values associated with them into characters.
    *   This means that if you enter an integer, lets say my age of 28, it is converted into the characters 2 and 8.
    *   If I wanted to store this as an integer with the value of 28 instead, I would need to convert the output string character by character to a numerical value. This is where the scanf() function comes into play.
*   Like printf(), scanf() takes in a control string followed by a list of arguments or parameters.
    *   Whenever we say the control string, we mean the destination data types for our input stream of characters.
*   Printf() uses variable names, constants, and expressions as its argument list, while the scanf() function uses pointers to variables.
    *   Don't worry if you don't understand what a pointer is yet. We will dive deeply into this later.
*   There are also three rules for us to remember before we use scanf():
    *   Scanf() will return the number of items that it successfully reads.
    *   If you use scanf() to read a value for one of the basic variable types that we previously discussed, you will precede the variable name with an &.
    *   If you use scanf() to read a string into a character array, you do not have to use an &.
    *   A quick side note, though we will be going into it later, an & just stands for an address in memory. We need to use this when we are using pointers. There is nothing else regarding this though that I expect you to know at this time.
*   The scanf() function uses whitespace (newlines, tabs, and spaces) to decide how it will divide the input into separate fields.
*   The final idea to understand for scanf() is that it is essentially the inverse or opposite of printf(). While printf() will convert integers, floating-point numbers, characters, and C strings to text so that it is able to be displayed onscreen, scanf() receives text and convert it into a specific data type so that we may use it in our program.

Now let's use scanf() in a program. I am going to create a new project called Example2, and write our code here:

```cmd
mkdir Example2
cd Example2
mkdir bin
mkdir obj
mkdir src
type nul > src/main.c
code src/main.c
```

Now that we have created our folder structure, and have opened up our code. So let us go ahead and create some code that reads in a string and a numerical value from us:

```c
/*
 * Author: Wes Holden
 * Purpose: Read in some values from the user
 * Date: 03/25/2023
*/

#include <stdio.h>

int main(void) 
{
    char charName[50];
    int charHealth;

    printf("Enter a characters name, as well as there health value: ");
    scanf("%s %d", charName, &charHealth);

    printf("\n Your characters name is: %s and has a total health of: %d ", charName, charHealth);

    return 0;
}
```

Now there are a couple of things that we want to go over with this code before we run it:

*   When your program uses scanf() to gather the input from the keyboard, it will wait for you to input some text.
    *   On top of this, when you enter some text and press enter, the program will proceed to read the input itself.
*   Remember that scanf() expects the input to be in the same format as your provided. In our case, this was %s and %d.
    *   This means that your input has to be in the format of "string integer" with a whitespace separating the two.

Now, let's break down this above function so that you know what we are seeing. We first create an array of characters that can hold up to 50 characters. We use this to hold the string that we want to pass in. We then create a simple int called charHealth. Though this is just an example set of code, I went ahead and gave it a purpose, reading in some game character information, so that we can name our variables appropriately.

We then call the printf function and pass into it the string literal "Enter a characters name, as well as there health value: ". This is what will first be printed to the screen. Notice we do not pass a new line character of \n to it. This is because we want our input to start on the same line as our printf output. 

Next, we call the scanf function. Because we are expecting a string and a numerical integer, we pass in both %s and %d separated with a space. We then pass in the str variable we defined above and the address for our integer. Remember, because charName is just an array of chars, it does not need the addressed passed with it, but because charHealth is an integer, it does. 

The last statement is the printf statement to show off our inputs. We start this with a new line character in order to put this on a new line in our console. Next, we pass charName and charHealth using the formatters %s and %d as we did above.

One thing to keep in mind is that scanf() uses whitespace to divide our inputs. So if we type in Test 10, it will split it into Test for str and 10 for i. Try other versions of this such as Test10 1 and even T est 10 and see what it will output.

There is one caveat that I want to touch on with scanf() and formatters in general, and this will be good to just keep in your back pocket. When we get to using floating-point numbers, and especially floats, we will eventually also touch on doubles. Now we might remember that for a float we use %f as the formatter, but what do we use for double? Well for a double, we can't use %d as that is reserved for integers. Instead we use %lf, which stands for a long float. This is important to remember as doubles, though bigger than a float, tend to be more efficient and you should prefer it over a float itself. We will dive more into this in the next section though.

So let us go ahead and compile and run this:

```cmd
gcc src/main.c -o bin/main.exe
```

Remember, in order to actually view the end output we need to add an additional scanf() to stop the program temporarily. Go ahead and add it yourself and rerun the program.
