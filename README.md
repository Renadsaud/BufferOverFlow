# BufferOverFlow
Buffer over flow attack on 32-bit Linux machines. we will show how to get a shell, and find a way to obtain root shell. finally, we will use the brute-force approach to defeat the address randomization countermeasure on our 32- bit VM.

# What is Buffer Overflow
Buffers are memory storage regions that temporarily hold data while it is being transferred from one location to another. A buffer overflow (or buffer overrun) occurs when the volume of data exceeds the storage capacity of the memory buffer. As a result, the program attempting to write the data to the buffer overwrites adjacent memory locations.

## Example
a buffer for log-in credentials may be designed to expect username and password inputs of 8 bytes, so if a transaction involves an input of 10 bytes (that is, 2 bytes more than expected), the program may write the excess data past the buffer boundary.

# Buffer Overflow Attack
Attackers exploit buffer overflow issues by overwriting the memory of an application. This changes the execution path of the program, triggering a response that damages files or exposes private information. For example, an attacker may introduce extra code, sending new instructions to the application to gain access to IT systems.

# Types of Buffer Overflow Attacks
Stack-based buffer overflows are more common, and leverage stack memory that only exists during the execution time of a function.

Heap-based attacks are harder to carry out and involve flooding the memory space allocated for a program beyond memory used for current runtime operations.

# This project consists of 3 Task:

Task 1- we edit the given source code “exploit.py” so that the buffer overflow attack is successful.

Task 2- we ensure the shell is running as root.

Task 3- Defeat the Address Randomization applied by the operating system.

# Implementation
In task 1, We have an exploit code called “exploit.py”. we have adjust the variables of the program accordingly and fill in any missing code to fulfill the buffer overflow attack. After you finish adjusting the above program, we run it. After, We have generated the contents for “badfile”. Then we compile and run the vulnerable program "stack.c".
after we made the vulnerable program run,  we got to be able to get a shell.
$ id
uid=1000(seed) gid=1000(seed) groups=1000(seed)

---------------------------------------------------------------------------------------

In task 2, After we made the shell run as root. we got the following output:
VM# id
uid=1000(seed) gid=1000(seed) euid=0(root) groups=1000(seed)

---------------------------------------------------------------------------------------

In task 3, On 32-bit Linux machines, stacks only have 19 bits of entropy, which means
the stack base address can have 2^19 = 524, 288 possibilities. This number is not
that high and can be exhausted easily with the brute-force approach. In this task, we use such an approach to defeat the address randomization countermeasure on our 32- bit VM. First, we turn on Ubuntu’s address randomization using the following
command:
sudo /sbin/sysctl -w kernel.randomize_va_space=2
Then we used the shell script to figure out how to attack the vulnerable program repeatedly.


