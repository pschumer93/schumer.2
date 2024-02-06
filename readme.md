#Project_1
#Phillip Schumer
#CMP SCI 4760
#SPRING 2024

-------------------
Project 1: Overview
-------------------
**THIS PROJECT WAS WRITTEN IN C LANGUAGE**
Write a Makefile to compile two source files into two separate executables. One of the executables
will be called oss and the other executable will be called user. 
These executables will be generated by object files, which were generated by .c files.
    oss.c => oss.o => oss
    user.c => user.o => user
The user executable is never executed directly. Instead, oss will be launching that executable
 at various times. Your Makefile must compile and create these executables at the same time. 
 This required us to use the "all" command in your makefile.

------------
User Process
------------
The user will be called by oss, but can directly be called by the command line.
This command line executable will take in two  command line arguments; 
    1). One is the executable itself.
    2). The other is the argument. 
If you were calling user directly from the command line, you would call it like:
    ./user 1
    (1 would represent  the number of iterations the process will do)
Each iteration it will output its PID, its parents PID, and what iteration of the loop it is in.
The Process will then sleep for 1 second. 
After the sleep, the current iteration will call its PID, its parents PID, 
and what iteration of the loop it is in again.
    For Example, "./user 1" will output:

    USER PID: 2565038 USER PPID: 2563157 Iteration: 1 before sleeping
    USER PID: 2565038 USER PPID: 2563157 Iteration: 1 after sleeping

NOTE: You should test this by itself, but it will not be called by itself normally.
Potential Problems: If called directly like "./user 5" the PPID will be random, 
because the fork which is located in oss.

-----------
OSS Process
-----------
The oss will launched by the command line. This command line executable will contain seven arguments;
    1). One is the executable itself.
    2). -n
    3). proc
    4). -s
    5). simul
    6). -t
    7). iter

    Definitions
    proc = The total number of user processes to be called.
    simul = The total number of processes to be called  simultaneously.
    iter = The total number of iterations per process.
    -n = Call code for proc.
    -s = Call code for simul.
    -t = Call code fr iter.
    -h = Call code for HELP.

Your solution will be invoked using the following command:
./oss [-h] [-n proc] [-s simul] [-t iter]
Take for Example, "./oss -n 5 -s 3 -t 7."
    -This command will launch 5 user processes from oss. 
    -This will only allow 3 user processes to running at the same time.
    -Each user process will run 7 iterations.
If called with the -h parameter, it should simply output a HELP message.
This HELP will indicate how it is supposed to be run and then terminating.
For Example, "./oss -h" will output:
    Help: oss
    ---------
    FORMAT: ./oss -n proc -s simul -t iter

        proc = This parameter indicates the total number of user 'processes' you want oss to launch.

        simul = This parameter indicates how many user processes oss are allowed to be launched 'simultaneously'.

        iter = This parameter indicates the number 'iterations' to run inside each user process.

OVERALL EXAMPLE: "./oss -n 4 -s 2 -t 3" will output:

    USER PID: 2580617 USER PPID: 2580615 Iteration: 1 before sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 1 before sleeping
    USER PID: 2580617 USER PPID: 2580615 Iteration: 1 after sleeping
    USER PID: 2580617 USER PPID: 2580615 Iteration: 2 before sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 1 after sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 2 before sleeping
    USER PID: 2580617 USER PPID: 2580615 Iteration: 2 after sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 2 after sleeping
    USER PID: 2580617 USER PPID: 2580615 Iteration: 3 before sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 3 before sleeping
    USER PID: 2580617 USER PPID: 2580615 Iteration: 3 after sleeping
    USER PID: 2580616 USER PPID: 2580615 Iteration: 3 after sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 1 before sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 1 before sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 1 after sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 2 before sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 1 after sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 2 before sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 2 after sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 2 after sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 3 before sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 3 before sleeping
    USER PID: 2580637 USER PPID: 2580615 Iteration: 3 after sleeping
    USER PID: 2580638 USER PPID: 2580615 Iteration: 3 after sleeping

------------------------------
How To Compile And Run: Github
------------------------------
1). Download source file from github in the link given below.
        A). Github URL: https://github.com/pschumer93/schumer.1
2). Open under Command-Line Terminal.
3). CD into the schumer.1.
4). Type "make" in the command line to compile your program executables.
    A). user.c => user.o => user.exe
    B). oss.c => oss.o => oss.exe
5). Type "./oss -n [proc] -s [simul] -t [iter]"
6). Results will be given.

-----------------------------------------
How To Compile And Run: opsys.cs.umsl.edu
-----------------------------------------
1). Download Putty at link given below.
    A).https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
2). Once Putty is downloaded. Set to ssh, set the port to 22, and set the host name
to: "delmar.umsl.edu"
3). Delmar will launch. Give your UMSL username and password to gain access. You will be
redirected to your UMSL Delmar.
4). Once in Delmar, you must access your opsys.cs.umsl.edu account:
    A). Type: "ssh 'username'@opsys.cs.umsl.edu."
    B). Enter in your opsys password.
5). Once in opsys, CD into schumer.1.
6). Type "make" in the command line to compile your program executables.
    A). user.c => user.o => user.exe
    B). oss.c => oss.o => oss.exe
7). Type "./oss -n [proc] -s [simul] -t [iter]"
8). Results will be given.

--------------
Problems found
--------------
1). If user is called directly like "./user 5" the PPID will be random, 
because the fork which is located in oss will not be made.
2). opsys.cs.umsl.edu will now allow you to link your github account for online virtual repository.
    You can not verify your account as of August, 2021. My "git repository" is opsys git commits.
    These can be accessed by "git log" under my personal opsys account. You can also access the same files
    on gitlab. All github commits come from copied opsys files that were simply pushed to github for your visual.

----------------
Git Repositories
----------------
1). opsys.cs.umsl.edu
    A). Type: "git log" under my opsys profile to view online local repository commits.
        (NOTE: opsys.cs.umsl.edu will now allow you to link your github account for online virtual repository.
        You can not verify your account as of August, 2021.)
2). Github
    A). Type: https://github.com/pschumer93/schumer.1
