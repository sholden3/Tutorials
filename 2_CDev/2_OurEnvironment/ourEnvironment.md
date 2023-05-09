# Our Environment

Before we go on to setting up our environment, I want to talk aboutt why we are choosing the steps that we are. There are many routes we can take in order to setup our environment, and more importantly, the path that we ultimately choose here is more along the line of showing you how our program actually works.

Because of this consideration, we will not be using an IDE. Though in a real life situation, or job, you will more than likely use an IDE. We will instead be using Visual Studio Code as a text editor, and will run our commands to compile and run our code through either our command prompt, or eventually through a make file. This allows us to have a deeper understanding of what it takes to make our program.

At first, this may seem difficult to do, but it will have you come out much stronger as a programmer. As that is the ultimate goal here, this is the path that we are going to take.

# Visual Studio Code

The first thing that we need to do is grab Visual Studio Code. We can find it at https://code.visualstudio.com/download. As this isn't a Visual Studio Code course, and it is pretty easy to learn by itself, we will only be looking at grabbing the necessary extensions that you need.

Once you have Visual Studio Code installed, go ahead and run it. When it starts up, there will be a symbol on the left with three blocks, and a fourth flying off of it. 

![](extensions.PNG)

This is the button to manage your extensions. Go ahead and click this button, and search for the C/C++ Intellisense extension by microsoft. This will just make the process of coding in C much more enjoyable.

That is it for Visual Studio Code! It is pretty simple, and as I said, I recommend you diving deeper into a lot of the features for Visual Studio Code.

# Compiler

For the compiler, we are going to use Cygwin. More importnatly, we will be installing the GNU gcc complier, make, and gdb debugger. Cygwin is a collection of open source tools which allows us to emulate a unix environment within Windows. I use this as I am on a windows machine, and I like that sweet, sweet, unix functionality.

We want to install the setup-x86_64.exe from https://cygwin.com.

It's a pretty simple install process. Just follow the process by keeping the defaults. I normally choose to install for everyone, and put the local package directory in my users drive. For the mirrors, just choose whichever work for you or the first that is up. It doesn't matter. Now for the next screen, you will be selecting your three needed packages. First thing you need to do is change your view option at the top left to Full. This will show you all of the packages available. Next, follow the below pictures. This will show you how to set each of the three packages. Choose the latest version, or the version I have below:

![](CygwinSetup1.PNG)
![](CygwinSetup2.PNG)
![](CygwinSetup3.PNG)
![](CygwinSetup4.PNG)

Once you have these set, you can proceed with the actual install. Once the install is done, you can choose to create an icon on desktop or add an icon to start. You can keep these checked or not. It doesn't matter. Once you are ready click finish.

Now we just need to set up the path. You want to go to the path that you installed this to. For me it was on my C drive at cygwin64. Once you find this directory, open up the bin directory. My path is: ```C:\cygwin64\bin```.

Now right click on this pc, and click properties. From the properties menu, click advanced system. This will bring up a windom that has a button called Environmental Variables at the bottom. Click this button.

On the new screen, go to the section called system variables. In this section go to the variable Path. With this highlighted, click edit. In the new window, click the new button. This will add a new blank section. Click on this and paste the bin path for cygwin64. Click ok. Click ok on every window that you had open.

Now, if you open up your command window, you can type ```cygcheck -c cygwin``` and press enter. This will output your cygwin package information if done correctly.

Now, just check your gcc version. Type and run ```gcc --version``` in your cmd and make sure it outputs a gcc version. Mine outputted the following:

```bat
gcc (GCC) 7.4.0
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

Now that we have this setup, we want to go ahead and create some simple code. Typically an IDE will handle all of this, but for us we want to do it by hand. The reason why is that I want to make sure you understand what is happening under the hood here.

So we want to create our generic folder structure. Yours can change, but I would suggest setting it up like this for now:

/project (root project folder, has project name)
|
|____/bin (the final executable file)
|
|____/doc (project documentation)
|
|____/src (every source file)
|
|____/obj (where the generated .o files will be)
|
|____/lib (any library dependences)

Now this will get us up and running, but we will want to expand on this as time goes on.

So let's create our folder with the following commands by launching your cmd prompt, and changing your directory by typing in ```cd path/to/directory to put your project in and folder that you want.:

```cmd
mkdir ExampleProject
cd ExampleProject
mkdir bin
mkdir doc
mkdir src
mkdir obj
mkdir lib
```

The commands above stand for make directory and change directory. Over time you will learn these cmd commands, but for now just enter them in.

Now in this project, we want to create our c source txt file: 

```cmd
type nul > src/helloWorld.c
```

The ```type nul > src/helloWorld.c``` is telling us that we want to create a simple empty text file with a c extension. This will be our source file that we will write our program in.

Go ahead and add some simple code to this file. Don't worry about what it does at this time, we will go over this later. Do this by opening the file in visual studio code. We do this by typing the following line into our cmd:

```cmd
code src/helloWorld.c
```

Another thing to note is that once we are in visual studio code, we can make use of the integrated terminal built into it. I actually prefer this if possible. So now let us go ahead and type in the following into the program.

```c
#include <stdio.h>

int main()
{
    printf("Please Work");
    return 0;
}
```

The main purpose here is to simply show you how to compile your code.

Go ahead and cd into your project directory, and we will run the following command:

```cmd
gcc -S src/helloWorld.c -o obj/helloWorld.s
```

Here we are compiling our code. That is what the -S flag does, and it is the first step of our build process. This will generate a file with a .s extension, which is our assemply code. Now this is all it will produce. It will not link our files, and it will not create an executable.

We won't be going over assembly files, but you can take a look at the file created to see how our source code is converted into assembly.

The gcc is the compiler itself, and we pass it our src file first. The -o is a flag indicating where we want to land our output file. In our case, this output file is simply our assembly file. Let us land this in our obj folder, as this is where our obj files will eventually end anyways.

So now that we have our assembly file, and we know that there are no issues at that level, we want to compile this .s file into an object file with an .o extension:

```cmd
gcc -c obj/helloWorld.s -o obj/helloWorld.o
```

Now really quick, you may wonder if we have to pass the -o for our output file each time, and the answer is no. If we want ```gcc -c obj/helloWorld.s``` from the terminal, it would create an object file of the name helloWorld.o in the directory we want the command in. The issue is that we are calling all of these commands from the parent directory, and I want my code to be organized well. We will automate this later though so don't worry to much about it.

So now let us finally create our executable, with all the files that we want to link for it, which is our object files. In this situation, there is only one that we need to worry about, but in the future there will be many more:

```cmd
gcc -o bin/helloWorld.exe obj/helloWorld.o
```

This creates an executable in our bin folder with an .exe extension. Now if we run this, we will see a quick popup, and nothing else. The code is running, but it is executing too fast for us to notice. Let us add a ```scanf()``` to accept some input, therefore pausing our program:

```c
#include <stdio.h>

int main()
{
    printf("Please Work");
    scanf("%c");
    return 0;
}
```

Now let's go ahead and create our executable from this:

```cmd
gcc src/helloWorld.c -o bin/helloWorld.exe 
```

The above is just a quick way for us to run all of our steps and output our executable. Now if we run our executable, we will notice that it will now pause, and we can go ahead and hit enter to have it finish.

Now this should have the basics that we need to really proceed further for now. We will be diving more into the compiler and the different flags, as well as ways to automate this in the future. We will also move eventually to an IDE, but there is a lot of good that we can get by doing this for now. It does suck though, but I swear it is helpful.
