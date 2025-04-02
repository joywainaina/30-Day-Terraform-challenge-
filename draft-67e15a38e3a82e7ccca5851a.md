---
title: "#90DaysOfDevOps Challenge - Day2 - 
            Basic Linux Commands(1)"
slug: 90daysofdevops-challenge-day2-basic-linux-commands1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1742822073980/a206b8ac-cfcf-4677-8c18-cc6e260f141d.jpeg

---

Welcome to day 2 of our devops series. Today we will cover basic linux commands. Linux is the most common and the most preferred operating system for devops workloads. This command will be used to create infrastructure and navigate various tools among other functions.

Let’s explore some of the common linux commands that we’ll come across!

## Getting help commands

We will always stumble across tools whose optional parameters we do not know from our own memory or tools we have never seen before. Therefore it is vital to know how we can help ourselves to get familiar with those tools.The first two ways are the man pages and the help functions. It is always a good idea to familiarize ourselves with the tool we want to try first.

### Help command

The help command can be used as - - help or -h depending on preference.

Usage:

```bash
<username>@<hostname>[~]$<tool> --help
```

### Man command

The man command displays the manual pages for commands and provides detailed information about their usage.

Usage:

```bash
<username>@<hostname>[~]$man <tool>
```

### Apropos Tool

Each manual page has a short description available within it. This tool searches the descriptions for instances of a given keyword.

Usage:

```bash
<username>@<hostname>[~] apropos <keyword>
```

## Listing Commands

The ls command lists directory contents.

Usage:

```bash
<username>@<hostname>[~]$ ls <optional argument> <file>
```

### Arguments used in the list command.

* ls -l &gt;list the files and directories in long list format with extra information
    
* ls -a &gt;list all including hidden files and directory
    
* ls -d &gt;list only directories
    
* ls -i &gt;list the files and directories with index numbers inodes
    
* ls \*.sh &gt;list all the files having .sh extension.
    

## Directory Commands

These are commands meant to manipulate directories.

* pwd &gt; print work directory. Gives the present working directory.
    
* cd path\_to\_directory &gt; change directory to the provided path
    
* cd~ or cd &gt; change directory to the home directory
    
* cd - &gt; Go to the last working directory.
    
* cd .. &gt; change directory to one step back.
    
* cd ../.. &gt; Change directory to 2 levels back.
    
* mkdir directoryName &gt; to make a directory in a specific location
    

Example working:

Make a nested directory.

```bash
mkdir -p A/B/C/D
```

## Conclusion

Linux is a very exciting operating system to use, as each day you stumble across a new amazing set of commands that makes your experience easier. In the next article, we will be covering more linux commands in this ecosystem.

See ya!