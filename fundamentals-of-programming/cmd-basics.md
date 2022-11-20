# Command line basics

Knowing how a terminal works is essential for any developer. This document is meant as a quick recap or re-introduction to the very basics already discussed in class.

It will follow the structure of the [class exercise](https://moodle.wsuf.hu/mod/assign/view.php?id=786) just as we did during the exercise session.

We will go through the same exercises on both Windows, and through the git-bash command line on a linux-like system as well.

More in-depth discussion of useful commands and utilities in linux will come at a later time. Now we will focus on certain commands on a need to know basis. Lastly, the capabilities of what we can do now with git-bash is also limited.

## 1. Windows command line basics

If we enter "cmd" from the start menu, the default folder it will have opened is the Home of the currently logged in user, which will suffice for now. In a few minutes we will learn how to navigate between them.

### 1.1 creating and removing directories

We start by creating a directory in which we will work throughout the first exercise.

```
mkdir exercise1
```

This created the folder named "exercise1".
As ```mkdir``` is an abbreviated short for "make directory" we also have its counterpart that is ```rmdir``` for removing a directory. The usage is the same.

```
rmdir exercise1
```

As now we no longer have the directory, we need to recreate it again. Luckily enough, we already know how:

```
mkdir exercise1
```

### 1.2 showing directory contents, changing working directories

A useful command to know is ```dir``` which displays a list of a directory's files and subdirectories.


> PRO TIP: you can learn about commands and their parameters from either the [official Microsoft knowledge base](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dir), or running the command with the /? parameter.

Continuing on with the abbreviations, we have ```cd``` that stands for "change directory". Enter the folder we just created:

```
cd exercise1
```

### 1.3 creating directory hierarchies

With mkdir, we can create multiple folders all at once by supplying it with a space or comma separated list.

```
mkdir dist, src
```

Also hierarchies:

```
mkdir src\blueprints src\models src\models\database
```

> Now it is your task, to create the second half of the structure. Templates and its subdirectories.

<details>
    <summary>solution (<i>click to expand</i>)</summary>

```
mkdir src\templates src\templates\auth src\templates\index
```

and

```
mkdir src\templates\auth\login src\templates\auth\register
```

...obviously there are many different ways to achieve the same.

</details>

### 1.4 navigating locally and globally

With our known commands, we are not limited to the current working directory. Most of them work either locally or globally on the whole system.

Let's say we are in the ```exercise1\src``` folder. First we enter it

```
cd src
```

Then create a folder back at the ```exercise1``` folder. We can do it from here, without having to change directories back.

```
mkdir ..\data
```

The double dot ".." at the start means the parent directory, or one directory up.

This functionality is the same with ```cd```.
Typing 

```
cd ..
```

will go one folder up in the hierarchy and we arrive back to the ```exercise1``` folder.

Another useful prefixes are the backslash ```\``` which means the root of the current system partition (`C:\` for example) or we can use a global path as well by specifying the whole path the following way listing the contents of the `C:\Users` folder.

```
dir C:\Users\
```

Lastly, if we want to set the current working directory to another partition, cd needs the `/d` option.

```
cd /d d:\
```

![folders](https://i.imgur.com/LEaUHul.png)

### 1.5 creating, reading and deleting files

Getting back on track, our next subtask in the first exercise is creating files.
Of course we can do them visually through some editor like Notepad or VSCode, but through the command line is another option.

> Let's confirm your current working directory first, check if you are at the right place, and if not, navigate back with CD as we have learned.

A command to create a file (or read a file) is ```type```:

```
type nul > .gitignore
```

> We will learn about this later, in a nutshell, we redirect the output of the first command to a file. So from the type command to the .gitignore file in this case.

> Nul is also a special type of file that discards all data written to it while also returning nothing when prompted.

Therefore the command above creates an empty file named ```.gitignore```.

If we want to create another file that has actual text content inside, ```echo``` will be our friend.

```
echo #this is a readme file > README.md
```

This creates the file README.md while also setting its contents to "#this is a readme file".

Listing the directory contents, they are there alright.

![img2](https://i.imgur.com/cfOvXer.png)

As mentioned, ```type``` can also be used to read contents of a file. For example:

```
type README.md
```

To delete a file, the command we need is ```del```.

```
del .gitignore
```

And with that, our ```.gitignore``` file is no more.

> There are various other useful symbols in cmd. One notable is ```&```. If we put it between two commands, it will execute both.

> What would happen if I were to type the following? ```mkdir folder & cd folder & mkdir ..\folder2```

<details>
    <summary>solution (<i>click to expand</i>)</summary>

Creates a folder named ```folder```, enters it, then created another subfolder named ```folder2``` back in the parent folder (notice the ..\ at the start) right next to ```folder```.

</details>




---
## 2. Linux command line basics