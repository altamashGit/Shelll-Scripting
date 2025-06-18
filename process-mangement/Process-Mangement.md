**Linux Process Management**
## Overview

## Welcome to my repository!

In this repository, we will explore process management in Linux. 
We'll do hands-on practical exercises in the terminal to learn interactively.

Throughout the exercises, you'll find screenshots to help you verify
that you're on the right track when executing commands.

At the end of the repository, we’ll create a cron job.
I’ll also create another repository named task.md, 
where I will assign a task for you to perform based on what you've learned here.

## 1. Understanding Processes
let's understand what is process, A process is any running program,
like a command or app, with a unique PID (Process ID), 
a parent process (PPID), a user, and a state (e.g., running, sleeping).



## Types of Linux Processes
**Foreground Process** – Runs in the terminal and requires user interaction.

**Background Process** – Runs behind the scenes without blocking the terminal.

**Daemon Process** – A background service that starts at boot and runs silently.

**Zombie Process** – A completed process that still remains in the process table.

**Orphan Process** – A process whose parent has exited, adopted by init or systemd.

## Process Management Basics
let's do some hands'on and see the command output and understand key component....!
## ps – Process Status
 1. The ps (process status) command is used to display information about
 currently running processes on your system.

```
ps
```
(image1)

Here, PID shows the process ID of bash and ps command tty shows that which terminal or emulator i'm in in your case
probabely it could be in pts/0.
 
 2. Now use some options(flags) to modify tge behavior of ps (process status).
```
ps aux
```
(image2)

Here, some overview of flags aux 
a → Shows processes from all users (not just the current user).

u → Displays processes in a user-friendly format (with details like CPU%, MEM%, etc.).

x → Includes processes not attached to a terminal (like daemons and background processes).

Understand the important fields you can see into your terminal or in the screenshot.
PID – Process ID

%CPU / %MEM – CPU and memory usage

TTY – Terminal associated (if any)

STAT – Process state (e.g., R for running, S for sleeping)

COMMAND – The actual command being executed.

 3.Find a specific process, whatever you want to find.

 ```
 ps aux | grep firefox
 ```
This show that process with full details.

 or

 ```
 pgrep firefox
 ```
 This show running process without any extra details.

  (image3)

 Both of these comaands filters and shows only processes related to specific process in our case here is ssh.

##  Understanding Process Status Codes (STAT)
R (Running) – Process is actively running or ready to run on the CPU.

S (Sleeping) – Process is idle, waiting for input or an event to occur.

D (Uninterruptible Sleep) – Waiting for I/O; cannot be killed until it's done.

T (Stopped) – Process has been paused (e.g., by Ctrl+Z or a debugger).

Z (Zombie) – Process has finished, but its parent hasn’t collected its exit status.

X (Dead) – Process is terminated and no longer exists (rare to see).

##  2. Managing Processes
Now you are able to view processes,Let's jump on the next step where we
are going to learn how to manage processes--Like Stoping,Resuming, or changing their pririty

Let's try a simple example. 
I'm going to start a process that just sleeps for a while in the background. Don't worry about this command's details; just know it creates a process.

```
sleep 600 &
```
make a note of number in the brackets,the second number is the pid of our sleep process.

(image4)

Now, let's use ps aux | grep sleep to confirm it's running and see its PID.
```
ps aux | grep sleep
```
(image5)

Okay, Now we are going to stop this process using kill command followed by it's PID.

```
kill <YOUR_SLEEP_PID>
```
(image6)
"Now, if you check ps aux | grep sleep again, it should be gone! We just 'killed' it gently.

```
ps aux | grep sleep
```
(image7)

## 3.  Background and Foreground Processes & Jobs
  - **Foreground Process**
  Runs directly in the terminal and blocks further input until it finishes.
  for example
 ```
 ping google.com
 ```
 You can see that your terminal is busy with this command.For stop press on your keyboard
 ctrl+c.

  - **Background Process**
  Now,If you want to run program in your terminam but you don't want it to take over your terminal.
  you can use (&) ampresand at the end of command to run it in the background.
  for example:----
  
  ```
  sleep 300 &
  ```
  To see what jobs running in the background use jobs command:
  
  ```
  jobs
  ```
  It lists our background jobs.
  Notice that bracket [1]+ this is a job number.

  (image8)

   - What if you want to bring a background process back into the foreground,
   so it takes over your terminal again? for this task we'll use the fg command,
   using with job number (from jobs command)

   ```
   fg %1
   ```

   (image9)

   "Now our sleep command is back in the foreground. You can press Ctrl + C to stop it.
   and ctrl+z to pause and sent it to the background.

   - Same thing we can do after it stoped we can run it again through the bg command 
   to run it into the background.
   
   ```
   bg %1
   ```
   
   (image10)
  look how stoped program send to the background running state.


## 4. Process Priority & Niceness
In Linux, processes have priorities that determine how much CPU time they get. 
You can control this using niceness values.
Think of it like a queue at a grocery store. If someone has a 'priority pass,' they get served faster. In Linux,
we can give processes a 'priority pass' or tell them to be 'nicer' and wait their turn.

Now get familiar with the Niceness what is it and how it works...

 **What is Niceness?**

Niceness (nice value) is a user-space mechanism to influence process priority.

It ranges from -20 (highest priority) to 19 (lowest priority).

The lower the nice value, the more priority the process it has.

- How to manage 'Niceness'
 Go to terminal and type:
```
nice -n 10 slep 300 &
```

(image11)
 
 It will start in the background with a nice value of 10 (lower priority).

 renice – Change the Priority of a Running Process

```
sudo renice -n 5 -p <PID>
```
(image12)

## Scheduling Tasks with cron (Cron Jobs)
A cron job is a scheduled task listed in a crontab (cron table) file. These tasks run in the background.


Basic Cron Syntax

```
* * * * * command_to_run
│ │ │ │ │
│ │ │ │ └─ Day of the week (0 - 7) (Sunday = 0 or 7)
│ │ │ └─── Month (1 - 12)
│ │ └───── Day of month (1 - 31)
│ └─────── Hour (0 - 23)
└───────── Minute (0 - 59)
```

Let's make a shell script for cronjob
 1.Create a file called helo.sh and give a executable permission:
I am using symbol ~ for creating my file into the home directory. 
 
 ```
 echo 'echo "Hello from cron at $(date)" >> ~/cronlog.txt' > ~/hello.sh
chmod +x ~/hello.sh
```
(image13)

 2. Add to crontab to run every 2 minutes

```
crontab -e
```
if you are using this command first time then you might get options to Select an editor then select nano at 1st place.
then add :-----

```
*/2 * * * * /home/yourusername/hello.sh
```
ctrl+s and ctrl+x save and exit

(image14)

 3. After a few minutes, check the log:
```
cat ~/cronlog.txt
```
(image15)



 ## 🥳 Congratulations!
🎉 You just created your first Cron Job!
You're now automating tasks like a true Linux user. Whether it's backups, monitoring, or periodic scripts — you've taken a big step in mastering process automation.


## What's Next?
Just head over to the 👉 task.md file in this repository.

There, a task is assigned for you to practice what you've learned — including process commands, job control, and cron jobs.

🎯 Do hands-on exercises yourself to reinforce your learning.
✅ Follow the instructions, try commands on your terminal, and track your progress.
