---
title: Zombie Process Creation and Handling
categories:
  - linux
tags:
  - linux
abbrlink: 60836
date: 2023-10-04 14:56:30
---

Zombie Process is a child process that has finished execution in the operating system, but its parent process has not yet called wait() or waitpid() to get its termination status. When a process ends, the operating system will keep some basic information of the process, including process ID (PID), exit status, etc. for the parent process to query. And if the parent process does not take the initiative to call the above function to retrieve the status of the process, then the information of this process will always exist in the operating system's process table, becoming a zombie process.

The following is a code that generates a zombie process

```
void fork7() {
    if (fork() == 0) {
        /* Child */
        printf("Terminating Child, PID = %d\n", getpid());
        exit(0);
    } else {
        printf("Running Parent, PID = %d\n", getpid());
        while (1); /* Infinite loop */
    }
}
```

![Snipaste_2023-10-04_14-58-43](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310041459960.png)

where the child process has completed execution, but information about the child process still exists in the process table. , and is displayed in the defunct state, i.e., the zombie process.

![Snipaste_2023-10-04_15-00-09](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310041500876.png)

wait() and waitpid() are system call functions used to wait for a child process to terminate in the parent process and obtain its termination status.

The roles of these two functions include:

1. Wait for the termination of the child process: the parent process can use the wait() or waitpid() function to pause its own execution and wait for the child process to end. The parent process will block on this call until the child process terminates.

2. Get the termination status of the child process: When the child process terminates, the operating system passes the exit status of the child process to the parent process. The parent process obtains the termination status of the child process by calling wait() or waitpid(), and can perform subsequent processing based on that status. The termination status can contain information such as the exit code of the child process, the reason for termination, and so on.

```
pid_t wait(int* status);
```

- The `status` parameter is used to hold the termination status of the child process. By checking the value of the `status` variable, the parent process can learn the termination status of the child process.
- The `wait()` function returns the PID of the terminated child process, or -1 if there is an error.

```
pid_t waitpid(pid_t pid, int* status, int options); 
```

- The `pid` parameter is used to specify the ID of the child process to wait for. when specified as -1, it means to wait for any child process to terminate.
- The `status` parameter is used to save the termination status of the child process.
- The `options` parameter is used to set additional options, such as WNOHANG for non-blocking wait.

The return values of the `wait()` and `waitpid()` functions can provide some information:

- Returning a value greater than 0 indicates the PID of a terminated child process.
- A return of 0 indicates that the WNOHANG option was used and that there are currently no terminated child processes.
- A return of -1 indicates a call error, possibly due to a permission problem or an invalid argument.

```
void fork9() {
    int child_status;
 
    if (fork() == 0) {
        printf("HC: hello from child\n");
    } else {
        printf("HP: hello from parent\n");
        wait(&child_status);
        printf("CT: child has terminated\n");
    }
    printf("Bye\n");
}
```

The parent process pauses its own execution by using the wait function to wait for the child process to finish, and the parent process blocks on this call until the child process is terminated

![Snipaste_2023-10-04_15-03-43](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310041503405.png)