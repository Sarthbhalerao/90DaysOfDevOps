# Linux Architecture

Linux architecture is a layered structure that defines how users, applications, and hardware interact with each other. Each layer has a specific role, making the system secure, stable, and efficient.

**1. Kernel**

-	Core of the Linux OS

-	Manages CPU, memory, processes, devices, and networking.

- Acts as a bridge between software and hardware

-	Prevents conflicts between running programs

-	Kernel Types: Monolithic, Microkernel, Hybrid, Exokernel

**2. System Libraries**

-	Provide common system functions to applications

-	Allow apps to interact with kernel without direct access

-	Contain reusable, pre-written code

**3. Shell**

-	Command-line interface for users

-	Accepts and executes user commands

-	Acts as a link between user and kernel

**4. System Utilities**

-	Built-in tools for system management

-	Used for installation, monitoring, user & file management

-	Simplify administration tasks

**5. Hardware Layer**

-	Physical components of the system

-	Includes CPU, RAM, Disk, I/O devices

-	Interacts with kernel using device drivers

# **What is User Space?**

-	Where users and applications run

-	Includes shell, system utilities, libraries, and applications

-	Communicates with kernel using system calls

-	No direct access to hardware (for safety)


# **Init / systemd:**

Init/systemd is the first process started by the Linux kernel that manages system boot and services.

**•	Init:**

-	It is the first process started by Linux kernel, having proceed ID 1 (PID 1)

-	It is responsible for starting system services during boot process.

-	Manages system runlevels (old systems)

-	A runlevel defines what state the system is in and which service should run, common runlevels are given below

      •	0 → System shutdown
      
      •	1 → Single-user mode (maintenance)
      
      •	3 → Multi-user mode (no GUI)
      
      •	5 → Multi-user mode with GUI
      
      •	6 → Reboot
 
**•	Systemd:** 

-	It is the modern replacement for init, having proceed ID 1 (PID 1)

-	Starts services faster using parallel execution

-	Manages system boot, services, daemons, and resources

-	Uses units (service, socket, timer, target), some common systemd units are given below:

    •	Service unit (.service)
    
    > Manages and controls background services like nginx and docker
    
    •	Socket unit (.socket)
    
    > Activates services when network or socket requests are received
    
    •	Timer unit (.timer)
    
    > Schedules and runs tasks automatically (alternative to cron)
    
    •	Target unit (.target)
    
    > Groups multiple services together (replacement for runlevels)


**Why it matters:**

-	Faster boot time due to parallel startup

-	Better reliability with automatic service recovery

-	Centralized service management (start, stop, status)

-	Replaces older tools like SysVinit, cron, runlevels

-	Essential for servers, cloud, and DevOps environments

-	Controls services like Docker, Kubernetes, Jenkins

-	Used for service automation and monitoring

-	Improves system stability in production environments


# Linux Process States:
A process state tells us what a process is doing at a particular moment in the system.

**1. Running (R)**

  -	The process is currently executing on the CPU
    
  -	Or it is ready to run and waiting for CPU time
    
  -	Example: a command actively performing calculations
    
  -	Means: Process is active
    
**2. Sleeping**

  - The process is not running right now because it is waiting for something.
    
**a) Interruptible Sleep (S)**

  -	Waiting for an event like:
    
  -	Keyboard input
    
  -	File read
    
  -	Network response
    
  -	Can be stopped by signals
    
  -	Example: waiting for user input
    
**b) Uninterruptible Sleep (D)**

  -	Waiting for critical I/O operations (disk, hardware)
    
  -	Cannot be interrupted until the task finishes
    
  -	Example: waiting for disk read/write
    
  -	Many D states indicate I/O or disk problems
    
**3. Stopped (T)**

  -	Process execution is paused
    
  -	Usually stopped manually or by a debugger
    
  -	Example: user presses Ctrl + Z
    
**4. Zombie (Z)**

  -	Process has finished execution
    
  -	Parent process has not yet collected its exit status
    
  -	Process remains only as an entry in process table
    
  -	Means: Dead process, but not fully cleaned
    
**5. Dead (X)**

  -	Process is completely removed
    
  -	No longer exists in the system
    
  -	Rarely visible to users
    
  -	Means: Fully terminated

# 5 Linux commands that will use daily:

**cd** 

> It is used to change the directory.

**pwd**

> It is used to get the present working directory.

**ls**

> It shows the list of files and directories in the present working directory

**mkdir**

> This is used to create a new directory.

**cp**

> It is used to copy files and directories from one location to another.

**mv**

> It is used to move or rename files and directories from one location to another.

**rmdir**

> It is used to remove the empty directory.















































