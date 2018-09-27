# Instructor Notes: Intro to the Command Line

### Lesson Outline

* Understand shells and UNIX philosophy
* Use bash to navigate a filesystem
* Use bash to conduct basic file operations
* Explain what dotfiles are used for
* Customise the look and feel of the powershell and windows command prompt.

### Unix

Unix is a family of multitasking, multiuser operating systems that derive from the original AT&T Unix, developed in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others.

Initially intended for use inside the Bell System, AT&T licensed Unix to outside parties from the late 1970s, leading to a variety of both academic and commercial variants of Unix from vendors such as the University of California, Berkeley \(BSD\), Microsoft, IBM and Sun Microsystems \(Solaris\). The UNIX trademark passed to the industry standards consortium The Open Group, which allows the use of the mark for certified operating systems compliant with the Single UNIX Specification \(SUS\). Among these are Apple's macOS which is the Unix version with the largest installed base as of 2016, and various flacours of Linux, which power most web servers.

From the power user's or programmer's perspective, Unix systems are characterized by a modular design that is sometimes called the "Unix philosophy", meaning that the operating system provides a set of simple tools that each perform a limited, well-defined function, with a unified filesystem as the main means of communication and a shell scripting and command language to combine the tools to perform complex workflows.

### Shells

A Unix shell is a command-line interpreter or shell that provides a traditional Unix-like command line user interface. Users direct the operation of the computer by entering commands as text for a command line interpreter to execute, or by creating text scripts of one or more such commands. Users typically interact with a Unix shell using a terminal emulator.

There are three shells used commonly:

* **Bourne Shell** \(`sh`\) - Introduced in 1979, this is old and reliable, but lacks many of the features present in modern shells.
* **Bourne Again Shell** \(`bash`\) - The default shell on macOS and most Linux OS's, this is the one we'll be working with on the course.
* **Z-Shell** \(`zsh`\) - grew out of `bash` in the 1990's. Commonly used in indistry because of its wide feature-set.

### Terminal.app / Git Bash

Explain why the terminal is important:

* It is a mac or Windows app that allows us to load a shell.
* As developers, we'll use it loads. Literally all the time.

### File Systems

**On Whiteboard...**

* Talk over the Windows filesystem and draw it up on the board as a tree.
* Show the diagram of the UNIX filesystem and explain its similarities to Windows

![Unix Filesystem Diagram](assets/unixfs.png)

* Explain the mac filesystem and draw it up as a tree.
* Explain `/` and `~`, using the tree diagrams on the board.
* Eplain what an absolute path is using the diagrams on the board.
* Explain a relative path using the diagrams on the board.
* Explain `.` and `..` using the diagrams on the board.

Draw up a key on the board as a reminder to the students:

> `.` = Current directory `..` = Next directory up `~` = Home Directory \(`/Users/my-username`\) `/` = Root Directory \(equivelent to `C:/` on Windows\)

**On Laptop...**

Get the students to login and open the Terminal.

### Shell Commands

Reccomend that the students follow along in the terminal, but also take notes. We're going to cover a lot of different commands and concepts.

```text
pwd # Prints the current directory as an absolute path
ls # Lists the files and folders in the curent directory
ls -a # Shows all files, including ones that start with a dot. Explain dotfiles.
ls -l # Shows more information about the files
ls -l -a # Using more than one falg together
ls -la # A shorter way of using multiple flags

# Ask: Where do we find out about these flags?

man ls # Manual page for the ls command, shows available flags. Press q to leave pager.
```

### Working with files and folders

```text
ls # Look at the folders available
cd Desktop # Change into the desktop
mkdir something # Create a directory
cd something # Change into it
mkdir one two three four # Make four subdirectories
open . # Open the current folder (something)
```

Ask the students to get it up in Finder. Create some random files and directory structures using `touch`.

> **QUESTION**: Ask a number of questions about how to change between deep directories, reinforcing `.` and `..` at the same time. **Ensure the students understand absolute and relative paths.**

### Copying, Moving and Removing files

```text
cp
mv
rm
rmdir
rm -rf
```

Explain tha file extensions aren't important, and that all our files are empty at the moment.

### `echo`, `cat`, `head`, `tail` and output redirection.

```text
echo "something"
echo "something" > myfile.txt
echo ls > somefile.txt
cat somefile.txt
tail -1 somefile.txt
tail -3 somefile.txt
head -2 somefile.txt
echo pwd > somefile
echo "This is a line" >> somefile
echo pwd >> somefile
cat somefile
subl somefile
```

### Globbing and Spaces in Filenames

Explain how globbing works to act on multiple files, and that we can handle spaces in paths by quoting the path or escaping

```text
ls *.txt
rm *.txt
cd "dir with spaces"
cd dir\ with\ spaces
```

### Symbolic Links

```text
ln –s from two
```

### Other Commands

Explain these other commands:

```text
nano # Opens a simple text editor
vim # Open Vim, a powerful text editor
code # Open VS Code text in OSX
su # Swith to the root user (not allowed on OSX)
sudo # Run a command as the root user.
```

### Flags

Remind that most commands have a number of flags. Flags can usually be written in two ways, longhand or shorthand. Longhand flags usually have two dashes before them, while shorthand flags have just one.

```text
brew --version
brew -v
brew list

npm --version
npm -v
npm list
```

### Dotfiles

In unic, any file or folder whose name starts with a dot is considered a hidden file. We often use these to store configuration data. Most UNIX systems will have a lot of thes "dotfiles" in the home directory.

> **QUESTION**: What dotfiles and dotfolders do ou have in your `~`? What do you think they do? Have a look at some of them with `cat` or `subl`.

We can customize the bash shell in our `~/.bash_profile` file.

Explain what dotfiles are in general and show the dotfiles on your machine.

```text
alias foobar="echo 'Hello There'"
alias lswc="ls –la"
```

Save and `reload` and `lswc` or `foobar`.

We've just added two command aliases.

### Summary

Highlight the importance of knowing how to use the command line, particularly the basic stuff relating to paths, moving, copying and removing files etc.

### Exercises

> * Practice using the basic shell commands
> * Customize the functioning of your shell
>   * Use .bash\_profile.
>   * Don't just copy/paste without understanding.
>   * Think about why you are doing it
>   * Talk to each other on Slack

### Further Reading

* [The Codecademy Command Line Course](https://www.codecademy.com/learn/learn-the-command-line)
* [Julia Evans' tweets](https://twitter.com/b0rk)



