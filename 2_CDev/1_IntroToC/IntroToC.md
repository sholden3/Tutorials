# Intro To C

Now, for everyone who wanted to learn Python first, let me try to sale you my case here first. C gives us a good look into many of the core concepts of computer science. You may think that Python could cover this in the same way, and you would be pretty correct. The issue is that some things are simply abstracted away to a degree that it becomes harder to visualize what is happening in the background.

You may also ask yourself, why aren't we learning C++? It has more immediate applications than pure C. I will give it to you again, you make a point. The point is wrong, but it is almost right. The issue with C++ that doesn't exist with C is that C++ has a lot of moving parts and complexity with it. The C++ language is vast, and you will have to learn OOP from the beginning.

So while Python is simpler to learn, it does not give us that view into what is happening in the background that we need. C++ does in fact give us this view, but as the cost of far greater complexity. So instead, we will take the best of both worlds, and just start with C.

By the end of this, you will have an understanding of not only how to program, but the lifecycle of your program. You will have a basic understanding of the compiler, as well as what it means to link your files together. Will it be hard? Yes, it will be. I won't sugar coat anything with you.

You may see others that say that you can learn a language in a month, or you can land that software engineer position within 3 months. Those are bold face lies. You can learn a language within a month, but that is with an already established solid foundation in CS. You can also land a software engineer position after three months, but you need to have the most stellar portfolio anyone has ever seen.

In reality, if you do not have a degree, it may take a year plus to get that job. Most likely 2 to 3 years. Once again, you could get a position prior to this, but it may be at a company that you really do not want to work at. A company that cannot hold other talent for whatever reason. At that point, you are probably just writing scripts and nothing else.

Even if you want to just go into the data science sector, you need to understand Computer Science. I know plenty of data scientist who do not know Computer Science. They may have the title of data scientist, but they are not true data scientists.

Now before we dive into C, I will say one more thing. The process you will follow here I have created over the course of 3 years, with many more in the future. This is truly a passion project of mine. It is what I followed that helped me go from being a contractor, making 15,000 less than the person I will managing, to a software engineer/data scientist manager. This is the process that allowed me to nail my SWE 2 interview for one of the largest e-commerce retailers in the world. The reason I say this is that, once again, this will be a hard path to follow. Despite that, if you do follow it you will have a high paying job. You will be in demand. Just don't give up.

Last word. You do not have to be smart to be a computer scientist. I am not smart. What you need to be is diligent. So don't give up. Hope to see you at Google one day.

## Fundamentals of a Program

The first step that we have to take in our journey into C is to define what a program is, what it does, and how it relates to what we are going to be doing.

The first thing I want to bring up is the fact that computers are dumb. Exceptionally dumb. A computer has to be led to the correct answer. You have to tell it exactly what to do and how to do it.

To typically portray this, many classes have you follow the peanut butter and jelly sandwich exercise. This portrays the typically process you will have to go through with an algorithm. This involves someone telling you how to make a peanut butter and jelly sandwich, and you have to follow it exactly. If they tell you to put the jelly on the bread, you put the whole jar of jelly on the loaf of bread. This may seem like an exaggeration of how it is developing an algorithm. Let me tell you it is not. Most of the time, creating an algorithm is either researching what steps you need to take, or trial and error until you have all steps down in as clear of steps as possible.

Ultimately we use this to show the importance of being specific with your instructions if you want to get the results you are expecting. The operations we use to create our instructions will go on to create the computer's instruction set. This instruction set contains the instructions that our cpu will execute. Remember that the cpu is our central processing unit, and not only does it execute our instructions, but it is in charge of most of our computing work.

Now, you may ask what this all has to do with our program, but just follow along and yuou will see.

So while we are bringing up the cpu again, let's just do a quick recap of some other computer hardware and software that are important. When it comes to the actual storage of the data used by our program, we utilize the RAM (random access memory). This is important to remember because you can have all the hard drive space in the world, the 2 TB of space on your ssd, it does not matter if you do not have enough ram. If you are a gamer, or a graphic designer, you may already be well aware of this.

On the topic of ram, our hard drive is completely separate from our ram. While our data in our ram exists as long as the program utilizing it does, our hard drive is our permanent storage. It will persist after our program is done running, or after our computer has been shut off. When you open a file from your directory, you are accessing it from the hard drive.

We then have our operating system, or O.S.. We utilize our operating system to make it more convenient for us to use the computer. The operating system is just a program that is responsible for the entire operation of our computer. It will handle all of our inputs and outputs, and it will manage the computer's resources, and handle the execution of programs.

The last thing that we want to touch on before getting out of this tangent here is the idea of the fetch/execute cycle. We are going to dive into this more later, but I wanted to talk about it here as well. We can also call the fetch/execute cycle the lifecycle of our cpu. It is the process that fetches instructions from memory (using something called the register), and executes it (through the use of a loop). One gigahertz of cpu can do this roughly a billion times per second. We can see this illustrated below:

![](cpuLifeCycle.jpeg)

This will be really important later when we look at how to really optimize our codes efficiency.

The tangent is now over. Back to our discussion on what is a program. So to really break it down, for us to solve any problem using a computer, we have to provide a solution to the problem itself. We do this by sending our instruction directly to the instruction set. If we take this logic here, we can say that all a computer program does is send the necessary instruction set to solve any problem.

Now the actual approach, or method, used to solve the problem is the algorithm. Remember that this is the black box that we mentioned before. In our phone book example, the statements that we used to solve the problem of finding our friend becomes the actual program.

The method that we used, the divide and conquer method, is the actual algorithm. We then use a computer language so that we can express these instructions for our program in a format that our computer can read.

So how does our computer read these instructions? Well, to get into that, I want to break out the idea of high and low level languages.

We can view a high level programming language as a language whos goal is to abstract away a lot of the logic used in creating programs. The purpose of this is to create a language that is human friendly. This makes is much faster to actually create the program, as you are focusing on the problem at hand, and not how to translate it to the computer itself. This is opposite of low level languages, such as assembly and machine language, which.

C itself is a high level language that abstracts away many of the actions we would would have to provide to a low level language. This makes C much more human readable than something like assembly. We no longer have to worry about the steps taken by the cpu.

A perfect example is the difference between the following C program, and its equivalent in assembly:

C

```c
#include 

int main(void)
{
    printf("This is our first example code.\n");

    int numericType = 10;

    printf("The value of numericType is %d, and is stored at the address of %p\n", numericType, &numericType);

    return 0;
}
```

Assembly

```assembly
.file	"main.c"
.text
.def	__main;	.scl	2;	.type	32;	.endef
.section .rdata,"dr"
.align 8
.LC0:
.ascii "This is our first example code.\0"
.align 8
.LC1:
.ascii "The value of numericType is %d, and is stored at the address of %p\12\0"
.text
.globl	main
.def	main;	.scl	2;	.type	32;	.endef
.seh_proc	main
main:
pushq	%rbp
.seh_pushreg	%rbp
movq	%rsp, %rbp
.seh_setframe	%rbp, 0
subq	$48, %rsp
.seh_stackalloc	48
.seh_endprologue
call	__main
leaq	.LC0(%rip), %rcx
call	puts
movl	$10, -4(%rbp)
movl	-4(%rbp), %eax
leaq	-4(%rbp), %rdx
movq	%rdx, %r8
movl	%eax, %edx
leaq	.LC1(%rip), %rcx
call	printf
movl	$0, %eax
addq	$48, %rsp
popq	%rbp
ret
.seh_endproc
.ident	"GCC: (GNU) 7.4.0"
.def	puts;	.scl	2;	.type	32;	.endef
.def	printf;	.scl	2;	.type	32;	.endef
```

Here you can instantly see the difference in readability between the two. Our C program, which for many may be hard to understand, is way easier than the assembly equivalent.

This leads us to the compiler. In order for us to transform this human readable code into machine readable code, we make use of a compiler. A compiler is a program that translates our high level language source code into a detailed set of machine language instructions that our computer requires to run the program. So in short, our program is responsible for the high level thinking, and the compiler generates the tedious instructions to the cpu. You can think of this, in a way, as a project manager coming up with the aspects of a project, and the software engineer creating  the actual detailed steps to create the programs needed for the project. Or maybe a better example is an architect drafting up the design of the building, and the builder converting the design into a finished product.

A compiler will also check for us if our program has valid syntax for the language that we are compiling. It will typically find the errors and report them to you. It will also hold off from creating the executable until all errors are fixed, thus further shaming you and your incompetence. We will touch on this further when we talk about debugging.

This means that when we write our code, we have to follow the rules of that language.

Long story short, the gist of all of this is that our high level langauge is much easier to read and write than its low level equivalent.

When we actually start writing our program, any program, in any language, there are seven steps that we can take:

### Define our Programs Objectives

In this step, we need to have a clear understanding of the requirements of the program. This is the business problem that we are trying to solve. Though we can revisit this step as needed to change our requirements, we should have a generalized end goal in mind here.

### Design the Program

Here we want to figure our how we will meet and satisfy the requirements outlined for our program above. This could be the specific architecture we want to use, the design of the UI, the specific tech stack we want to utilize. Whatever we decide to do, it should align with both our expectations and our customers.

### Write the Code

This is where we start the implementation of our program. Here we translate the design to whatever language syntax that we choose. This is where we will use our C code and our editor to create our source code.

### Compile

In this step, we translate the source code into machine code, which is our executable code. This is the detailed instructions to the cpu that we want expressed in a numeric code.

### Run the Program

This is the creation of the actual executable file that you will run your program with.

### Test and Debug the Program

This is one of the biggest parts of your development lifecycle here, and in my opinion, one of the most neglected. Just because you completed your program and compiled it into your executable, it doesn't mean that you are finished.

In order to reduce cost later, in both man power and cost to your sanity, you need to make sure that you have implemented tests that ensure your code is running as expected. We call this debugging, which is the process of finding and fixing your program errors.

Don't worry about making mistakes, everyone does. It is a natural part of programming and development. Some cases, you may even purposefully implement mistakes while testing.

### Maintain and Modify the Program

When you are finally done debugging and testing your program, you can release it out into the world to be used by whomever your customers are.

One thing you need to keep in mind is that this tends to be the most expensive phase, as you will need to continuously fix any new bugs that come up, as well as add new features.

This is really the step that you can see the fruits of your labor from the previous step really come out and shine. You will probably have bugs that your QA engineer didn't catch, that is life, but you do not want to have a bad image with your customers.

These phases of development above are all important for the lifecycle of your program. You really can't skip any of them, atleast not in the real world. Any large scale application will require multiple developers, and often multiple teams, interacting together in unison. Because of this, you will need to have clear objectives, a clear design that you will use. You will need testing to ensure that your program has longevity, as real money and time will need to be allocated for your project.

There are cases, though, where you will touch on each of these phases above, but not necessarily in the order you see. We will touch on these methodologies later, but it is important to understand that we will still use each phase.

As we learn to program, we will use each of these phases, even for relatively short programs. The reason why is to ingraine this idea into our heads on how to be effective programmers.

Following this may take time, but it can help ensure that you have modular, well tested, decoupled code for your projects.

## Language Features Shallow Dive

At this point, we have a very basic idea over the anatomy of our program, but what about the specific features of C that make it a great first language? In this section we are going to dive into the four main features of C:

### It is Efficient

C was originally built to take advantage of the many capabilities of modern computers. This is something that we will see first hand when we look at the organization of a computer, and the lifecycle of a program.

C was also made to be very compact by having only the features the programmer needed. C doesn't have objects or classes, therefore it doesn't have the needed complexity for them either. It is also very fast, as it is built very close to the assembly language itself.

Utilizing these aspects of C, we are able to finely-tune our programs for maximum speed and efficient use of memory.

### It is Portable

We can easily port C programs from one system to another with very little to no modifications. We can do this without the use of a virtual machine in the background, like we would use for python or java. Ontop of this, we have C compilers available on most computer architectures (don't worry about this at this time, we will go into more depth on compilers and computer architectures later.)

### It is Powerful and Flexible

The Unix/Linux kernel itself is written in C. A kernel is just the main program driving an Operating System. Once again, we will dive more into this later. Many different compilers and interpreters for other languages are also written in C. Perfect example, Python is written in C. What this means is that if we want to write a quick and efficient library for these languages, we can do it in C and port it over. It is also a basis for the more advanced language C++, as well as many other advanced languages.

Because of this, C is widely used in many industries, as it can be used to develop just about anything you can imagine for your computer program.

This brings us back to why we want to learn C first. This compactness of C allows us to quickly get up to speed and create practical, but efficient applications quickly and easily.

### It is Programmer Oriented

C aims to fulfill all the needs of the programmer. Furthermore, unlike some other languages, we have the ability to control our program at a much more lower level. C gives us, the programmer, access to the hardware. This will be useful later on when we look computer organization. We are also able to manipulate individual bits in memory, which will be both a blessing and a curse, which you will see later on. This is mostly due to the fact that pointers play a huge role in C, as it gives us direct access to memory. This may be difficult at first, but eventually once you understand what is happening, will become second nature.

C also gives us a large selection of operators which allows us to express ourselves via our code. as well as a large library of C functions that allow us to deal with most problems we will run into. C is also less strict than most languages, which once again is both a blessing and a curse. Essentially, it gives us more freedom in what we are able to do, at the cost of greater responsibility.

Out of all of these features, though, three of them, in my opinion, really differentiate C from most other languages you will learn. These are:

*   Low level features provided by C.
*   The ability to manage memory representation at the bit level.
*   The use of pointers in giving us direct access to memory.

It is through these three core features of C that I believe makes it the perfect language to learn CS.

Now there are some noticeable disadvantages in learning C, especially for a new programmer.

The added flexibility and freedom granted to you through C can add an extra level of responsibilty to the programmer that they may not fully comprehend. By this, I mean that when dealing with memory, or interfacing directly with hardware, you may not be as disciplined, or have the knowledge yet, to fully understand what you are doing. Therefore, if you are reckless, you can cause damage.

The use of pointers also adds a level of complexity to our programming errors that may make it much harder to trace. This feeds into the above point, and we will go over how to mitigate this later, but it may seem much less intuitive than a language like Python at first.

You can also write very obscure code due to the large amount of operators present in C. This may seems like a weird point now, but when you compare your C code to Python code later, you will see what I mean by this.

Despite these facts, C is still an amazing language to learn, as very easy overall to understand.

# Basics of Creating a C Program

At this point, you should have a decent understanding of the basic features of C, and why it is a useful language to learn. Now, we need to actually look at the process of creating a C program.

Due to the low level nature of C, I personally believe that it would be helpful to first disect what a C program looks like before we write one. This helps to give us a very high level view of what is going on before we jump into it.

## Editing

This is the process of actually creating and modifying our source code itself. Typically when you think of programming, this is the step you think of. When we talk about source code, this stands for the actually file that contains the program caode that we are writing.

For the program file that contains our source code, you want to make sure you choose a meaningful name. It will also need to have a .c extension as well. If we were creating a file that contained mathematical functions, we would probably want to call it Math.c. If it contained graphical functions that we wanted to call for our program, we would probably call it Square.c or Lerp.c.

We further use sometype of editor to manipulate and change our source files. These can be complex like an IDE, or simple like a lightweight text editor.

## Compiling

The duty of a compiler is to convert our source code from our editing phase into machine language that our computer can understand. It also has the added feature of detecting a reporting errors that it may find in the process.

Compilation itself falls into two phases. The first phase is called the preprocessing phase, which our code is either modified or added to. The second stage is the actual compilation which generates the object code.

When we actually run the compiler, it will check each program statement in our file, and it will check to make sure that it follows the correct syntax and semantics of the language we are using. It will also check for dead code, which is simply structural errors in our code. Better said, this is code which is executed, but the results are never used.

One thing that the compiler will not do is check for logic errors. This means that if we misuse a pointer, or overwrite a variable, or incorrectly implement our algorithm, we will still need to fix this.

After all errors are fixed, the compiler will convert each statement in our code into assembly language. It will then take each assembly langauge statement and translate it into machine instructions and output this as the object code. The object files will have the same name as your source file, but will contain either a .obj or .o extension.

When it comes to compiling your code, there is a standard command which we can use. Now, you may not need to run this command depending on the IDE you are using, but in our class here, we will be running our programs by cmd. The command is called the cc (or the GNU compiler, which is gcc). This falls into the following commands:

```cmd
cc -c mycprogram.c
gcc -c mycprogram.c
```

If we omit the -c flag, our program will also be automatically linked. Which brings us to the next section.

## Linking

After the program has been translated into object code, we can then link it. The reason why we link our code is to make the code ready to be executed on our computer. This means that all of the external libraries and files we use need to be linked together so that our code will actually run.

Typically linking is an automatic process, but depending on what system we are on, or our ide, it can be its own command.

The linker will also combine the object modules generated by the compiler, and any additional libraries that we may need for the program to create our executable.

Furthermore, just like our compiler, the linking process has the ability to detect and report errors. This typically falls to finding any missing or nonexistent libraries taht are referenced.

To get back to program files, these are libraries that support and extend the C language by providing routines to carry out operations that are not part of the language itself. These can be, but are not limited to, input and output libraries, mathematical libraries, string manipulation libraries, and more.

A failure during the linking phase means that you need to go back to the editing phase, though many of the errors during the linking phase may simply mean that you forgot to add a library, or have a nonexistent library that you are referencing in your code.

If your linking phase is successfull, you will produce an executable file. If the program is complex, and large enough, there will be several source files generated. For each one of these, the compiler will need to generate an object file that will need to be linked. You may wonder why we don't have just one single source file to link, but the program is much easier to manage if we break it up into multiple smalelr source files. This allows us to keep our program modular. This means that it is much easier to develop our program over time, as well as maintain it. The source files that make up your program will also typically be integrated under the project name itself, which is used to refer to the program as a whole.

## Executing

This is the last step that we will take with our program. Typically, in most ide's, this will be a simple menu button or button click. Otherwise, you can just double click the exe file itself, or call it through your command prompt.

This step involves the actual running of our program, and each step is ran sequentially in our program. If data is requested from the user, the program will temporarily suspend its execution until the input is entered. Any outputs and results from the program that need to be displayed will typically be displayed in the console.

This stage can also produce error conditions as well. These can range from producing the wrong result, not executing, or even crashing your computer if you are not careful. If the program executes, but does not perform how you intend, then you will have to go back and re-analyze the core logic of the program. We call this the debugging phase, and you shouldn't be discouraged by this. For this, you will need to restart the process all the way back at the editing phase, until no more errors are found.

Now when we first start, this might seem unwiedly for you to follow everytime, but as you program more, you will memorize these steps.

As well as this, a lot of these processes will be used in any compiled language. The difference will be the steps, and to a degree, the automation of these steps within the language itself. Obviously we will be focusing on the steps specific to the C language.

Now that we have our essential steps down for what we have to do, we can move forward with setting up our environment to code in.
