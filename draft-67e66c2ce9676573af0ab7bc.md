---
title: "#90DaysOfDevOps Challenge - Day3 - 
            Basic Linux Commands(2)"
slug: 90daysofdevops-challenge-day3-basic-linux-commands2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1743154329809/27a35fb9-fae4-481f-9ad0-dedabdf4ddba.png

---

Welcome to day 3 of the devops learning path. From our last article, we discussed some of the linux commands used in our day to day activities. In this article, we will dive deeper into other commands also used to manipulate the terminal and perform tasks.

## Commonly used Command in Linux:

### System Information Commands.

* whoami - Displays current username.
    
* id - returns users identity
    
* hostname - Prints name of current hostname
    
* pwd - Prints the present working folder/directory.
    
* uname - Prints information of current operating system and system hardware.
    
* ip - utility to show or manipulate routing, network devices, interfaces and tunnels.
    
* ps - Shows process status.
    
* who - Displays who is logged in.
    
* env - Prints environment or sets and executes command.
    
* lsusb - Lists USB devices.
    
* lsof - Lists opened files.
    
* ifconfig - used to assign or to view an address to a network interface and/or configure network interface parameters.
    
* netstat - Show network status
    

### Working with files and directories

**Creating a file**

touch &lt;name&gt;

*touch myfile*

**Creating a directory**

mkdir &lt;name&gt;

*mkdir Students*

**Creating multiple directories within other directories(nesting)**

Use the -p flag(parent)

mkdir -p &lt;nested directories&gt;

*mkdir -p Students/grades/grade1/mercy*

**Looking at the whole directory structure**

tree &lt;directory name&gt;

*tree Students*

**Move or rename files and directories**

The move(mv) command can be used to move or rename files and directories.

mv &lt;file/directory&gt; &lt;renamed file/directory&gt;

mv &lt;file/directory&gt; &lt;moving location&gt;

**Copy file/directory from one directory to another**

cp &lt;file/directory&gt; &lt;destination directory&gt;

**Editing files**

Let’s move on to working with files. There are several ways to edit a file in Linux, with some of the most common text editors being *vi* and *vim*. However, we will start with the `Nano` editor, which is less commonly used but easier to understand.

**nano editor**

To create and edit a file using Nano, you can specify the file name directly as the first parameter when launching the editor. For example, to create and open a new file named notes.txt, you would use the following command:

```bash
nano notes.txt
```

The caret(^) at the bottom of the editor with some options stands for \[CTRL\] key.You can use the options to save the file, edit the file, search through the file etc.

**Vim editor**

Vim is an open-source editor for all kinds of ASCII text, just like Nano. It is an improved clone of the previous Vi. It is an extremely powerful editor that focuses on the essentials, namely editing text.

In contrast to Nano, Vim is a modal editor that can distinguish between text and command input. Vim offers a total of six fundamental modes that make our work easier and make this editor so powerful:

| **Mode** | **Description** |
| --- | --- |
| Normal | In normal mode, all inputs are considered as editor commands. So there is no insertion of the entered characters into the editor buffer, as is the case with most other editors. After starting the editor, we are usually in the normal mode. |
| Insert | With a few exceptions, all entered characters are inserted into the buffer. |
| Visual | The visual mode is used to mark a contiguous part of the text, which will be visually highlighted. By positioning the cursor, we change the selected area. The highlighted area can then be edited in various ways, such as deleting, copying, or replacing it. |
| Command | It allows us to enter single-line commands at the bottom of the editor. This can be used for sorting, replacing text sections, or deleting them, for example. |
| Replace | In replace mode, the newly entered text will overwrite existing text characters unless there are no more old characters at the current cursor position. Then the newly entered text will be added. |
| Ex | Emulates the behavior of the text editor *Ex* one of the predecessors of vim. Provides a mode where we can execute multiple commands sequentially without returning to Normal mode after each command. |

When we have the Vim editor open, we can go into command mode by typing ":" and then typing "q" to close Vim.Vim offers an excellent opportunity called vimtutor to practice and get familiar with the editor.Entering the tutor mode in vim editor can be done using the Command mode :Tutor or by using the vimtutor command in the shell.

### **Cat command**

Used to view contents of the file.

Usage:

```bash
cat notes.txt
```

### Top Command

### Difference Command

### Grep Command

### Sort Command

### Tail Command

## Conclusion

Linux has thousands of commands used to manipulate the shell. Understanding some of these commands is essential when dealing with various devops tools. Let’s connect in the next article!