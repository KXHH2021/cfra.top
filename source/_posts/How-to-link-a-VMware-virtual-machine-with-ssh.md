---
title: How to link a VMware virtual machine with ssh
categories:
  - tutorials
tags:
  - virtual machine
  - linux
abbrlink: 7310
date: 2023-10-04 22:28:06
---

## I. Configuration environment

1、VMware 15
 2、ubuntu-18.04.1-desktop-amd64
 3、Xshell7

## II. Configuration process

### 1. Is there any `ssh` configured in the virtual machine?

```
root@kqz-virtual-machine:/usr/bin/bin# /etc/init.d/iptables start
bash: /etc/init.d/iptables: There is no such file or directory.


```

This is because the ssh seat is not installed and the file or directory is not present.

### 2. Command to install ssh

```
root@kqz-virtual-machine:/etc# sudo apt install openssh-server


```

### 3. Restart the `ssh` service

```
root@kqz-virtual-machine:/etc# sudo service ssh restart


```

### 4. Turn on the default port number

Enter the code into the editor

```
root@kqz-virtual-machine:/etc# vi /etc/ssh/sshd_config
```

Release this port：

![Snipaste_2023-10-04_22-34-25](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042234893.png)

### 5. Save and exit `:q` Carriage return

![Snipaste_2023-10-04_22-34-39](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042235383.png)

### 6. Restarting the `SSH` service

```
root@kqz-virtual-machine:/etc# sudo service ssh restart
```

## III. Local `SSH` connection to the virtual machine

### 1.Find your own `IP` port for the `22` just now

![Snipaste_2023-10-04_22-48-07](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042249177.png)

### 2.Connecting with `root` user will fail to connect, but connecting with normal user will not report an error.

Solution: You can log in as an ordinary user and then enter the root user.

![Snipaste_2023-10-04_22-51-02](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042251129.png)