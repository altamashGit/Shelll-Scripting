# Shell Scripting Introduction

Welcome to the ***Shell Scripting Introdution** repository...!!

In this repo you are going to learn basic of the Linux Shell,with a Focus on Bash Scripting......!!

This repository is designed to help beginners learn the fundamentals of Linux shell scripting, 
with a focus on **Bash scripting**. Whether you're new to the command line or looking to automate tasks, this guide covers the essentials to get you started.


## Table of Contents
1. What is a Shell?
2. Interacting with the CLI
3. Basic Shell Commands
4. Standard Input, Output, and Error (stdin, stdout, stderr)
5. Types of Shells
6. Shebang
7. Writing a Shell Script
8. How to Run a Shell Script
9. Why Use Shell Scripts?

# 1. What is the shell........?

A *shell* is a *program* that provides a command-line interface for users to interact
with the operating system.
It interprets and executes commands you type.In a Text-Based Interface....!

let's understand first what is the interpreter Just assume that it's like a translator at live speech - 
it listens to each sentence and immediately converts it into the listener's language,
one line at a time, so the audience can understand as the speaker goes.

**How Commands Flow: From User to Hardware via Shell and Kernel***
Let's understand with the Analogy.......
“Think of the shell as a waiter at a restaurant — you (the user) tell the waiter (the shell) what food you want, 
and the waiter passes your request to the kitchen (the OS). 
Then the waiter brings back the result (the output).”

![Image](https://github.com/user-attachments/assets/547775b8-0afb-4009-a1b0-0a9af2a9ffff)

User: You, the person making a request.

Shell: Like the waiter — takes your request and passes it on.

Kitchen (OS): Prepares the food — i.e., processes your command.

Output (result): The food that comes back — the result you see on the screen.

  **Diagram idea**

  ![Image](https://github.com/user-attachments/assets/9823f52b-1e08-4595-82d3-926ab5a3a7ac)

[User] → [Shell] → [Kernel] → [Hardware]


#  2. Interacting with the CLI
If you say Shell = Command Line Interpreter (CLI) then it would no be
wrong.The shell reads the command you type. interperts it . and asks the operationg system
to execute it. 
The Command Line Interface (CLI) is a text-based interface where you tyoe commnads.
In Your LInux Just Click on the Terminal or in ubuntu you can press a short key
(alt+ctrl+t) to open a terminal.


#  3. Basic Shell Commands

 ls: List directory contents
```
ls
```
 cd: Change directory
```
cd
```
 mkdir: Create directories
```
mkdir
```
 rm: Remove files or directories(It Delete file permanently)
```
rm <file-name>
```
Try typing these commands in your terminal and observe what happens.
Just play around with them and see how the shell responds.


#  4. Standard Input, Output, and Error (stdin, stdout, stderr)
   . stdin (Standard Input) – where the program receives input (usually from the keyboard).
   
   ![Image](https://github.com/user-attachments/assets/dca0efd7-2719-4e65-8236-d055d7079961)
   
   . stdout (Standard Output) – where the program sends regular output (usually to the screen).
   
   ![Image](https://github.com/user-attachments/assets/f0c7bad5-3c0e-4dee-9e41-7808b01ffe03)

   . stderr (Standard error) – where a program prints errors (also usually the terminal).
   ![Image](https://github.com/user-attachments/assets/4122dcb2-3d94-4c26-b48e-1b6a7d36bb25)
  

  # 5. Types of Shells]
  “Different shells offer different features, scripting syntax, and performance optimizations.
   Think of them like different text editors or programming languages — they do similar things in different ways.”

   examples--:
  •	Bash (Bourne Again Shell) – Most common shell in Linux systems today sh (Bourne Shell)
  
  •	Zsh macOS-- Modern and highly customizable, popular on macOS.
  
  •	Ksh(Korn Shell)-- Fast and script-friendly, used in enterprise Unix systems.
  
  •	csh-- Less favored for scripting because of it uses C progamming syntex.
  
  To Check which Interpreter or Shell do you have:---
   ```
   echo $0

   ```
   either

   ```
   echo $SHELL

  ```

 # 6. Shebang (#!/bin/bash)

 **#!** — This is the special character sequence that tells the system, 
 "Use the following program to interpret this script."
Always Remember that ,This is always the very first line of a Bash script.
**/bin/bash** — This is the path to the Bash shell (Bourne Again SHell),
 which is a common command-line interpreter on Unix-like systems.

 # 7. Writing a Shell Script
 
 A shell script is a text file containing a series of commands that are executed by the shell,
 allowing you to automate tasks in a Unix/Linux system.

 Let’s write your first shell script------
  1.  open your test editor type nano and hit enter.
```
 nano
```
 2.Add this code:
 ```
#!/bin/bash
echo "Hello, world!"
echo "You're running your first shell script 🚀"
 ```
![Image](https://github.com/user-attachments/assets/275c3291-455c-48fd-b317-49ae80806784)

Then in your keyboard press ctrl+x write a name "script.sh" hit enter to save, then ctrl+x for exit.

#  8. How to Run a Shell Script

In your terminal type ls to confirm that file is save.
```
ls
```
then give a execute permission to the file with the help chmod command.

```
chmod u+x script.sh
```
To Run this script type this command into your terminal

```
./script.sh
```
![Image](https://github.com/user-attachments/assets/fd7dda2e-77ec-4874-8921-3cbcb49ab2f1)

# 9. Why Use Shell Scripts?

  1.  Automation – Run multiple commands or tasks with a single script.

  2.  Speed – Perform tasks faster than clicking through menus.

  3.  Powerful tools – Combine simple commands to handle complex tasks.

  4.  Remote control – Manage servers and systems over SSH.

  5.  Scripting – Write reusable code for backups, file management, and more.

  6.  Efficiency – Use fewer system resources compared to GUI tools.

  7.  Customization – Tailor your environment with aliases, functions, and scripts.
