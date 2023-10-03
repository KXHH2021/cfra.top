---
title: Python3 Installation
date: 2023-10-3 10:01:02
categories:
  - tutorials
tags:
  - Python3
description: Helps you install Python
---

## Python3 Installation

Python3's latest source code, binary documentation, and news can be found on Python's official website:

Python official website: https://www.python.org/

### Installing Python on the Window Platform.

Here are the simple steps to install Python on the Window platform.

Open a web browser and go to https://www.python.org/downloads/windows/ to download the executable installer, x86 for 32-bit machines and x86-64 for 64-bit machines.

Press **Win+R**, type cmd to bring up the command prompt, and type python:

![Snipaste_2023-10-03_11-57-54](https://cdn.jsdelivr.net/gh/KXHH2021/yyyyn@mian/img/202310031202508.png)

### Installing Python3 on Unix & Linux platforms.

The following are simple steps for installing Python on Unix & Linux platforms:

- Open a web browser and go to https://www.python.org/downloads/source/

- Select the source tarball for Unix/Linux.

- Download and extract the tarball **Python-3.x.x.tgz**, **3.x.x** is the version number you downloaded.

- If you need to customize some options change *Modules/Setup* to

  Take **Python 3.10.11** as an example:

```bash
# tar -zxvf Python-3.10.11.tgz`

# `cd Python-3.10.11`

# `./configure`

# `make && make install`
```

Check that Python3 is properly available:

```
# python3 -V
Python 3.10.11
```

### Installing Python on a MAC platform.

MAC systems come with the Python 2.7 environment, and you can install Python 3.x by downloading the latest version at the link https://www.python.org/downloads/mac-osx/.

You can also refer to the source code installation.

## Environment variable configuration

Programs and executables can be in many directories, and these paths are most likely not in the search paths provided by the operating system for executables.

The path is stored in an environment variable, which is a named string maintained by the operating system. These variables contain information about available command-line interpreters and other programs.

The path variable in Unix or Windows is PATH (UNIX is case sensitive, Windows is case insensitive).

On Mac OS, the installation path for Python was changed during the installer. If you need to reference Python in another directory, you must add the Python directory to path.

### Setting environment variables in Unix/Linux

- **In the csh shell type: **

```
setenv PATH "$PATH:/usr/local/bin/python"
```

Press Enter.

- **In the bash shell (Linux) type :**

```
export PATH="$PATH:/usr/local/bin/python" 
```

Press Enter.

- **In the sh or ksh shell, type.**

```
PATH="$PATH:/usr/local/bin/python" 
```

Press Enter.

Note: /usr/local/bin/python is the Python installation directory.

### Setting environment variables in Windows

Add the Python directory to the environment variables:

In the command prompt box (cmd) Type :

```
path=%path%;C:\Python 
```

- Press "Enter".

  

  **Note:** C:\Python is the installation directory of Python.

  You can also set it in the following way:

  - Right-click on "Computer" and click on "Properties".
  - Right-click on "Computer" and click on "Properties", then click on "Advanced System Settings".
  - Select "Path" in the "System Variables" window, and double-click it!
  Double-click on it! 
  - Then in the "Path" line, add the path to the python installation (my D:\Python32), so after that, add the path. **ps: Remember, paths are separated by a semicolon ";"! **
  - After the final setup is successful, in the cmd command line, enter the command "python", you can have the relevant display.

![Snipaste_2023-10-03_12-16-52](https://cdn.jsdelivr.net/gh/KXHH2021/yyyyn@mian/img/202310031217338.png)

## Running Python

There are three ways to run Python:

### 1. The interactive interpreter:

You can enter Python through a command-line window and start writing Python code in the interactive interpreter.

You can code Python on Unix, DOS, or any other system that provides a command line or shell.

```
$ python             # Unix/Linux

or  

C:>python           # Windows/DOS
```

### 2. Command Line Scripting

Python scripts can be executed on the command line by introducing an interpreter in your application, as shown below:

```
$ python  script.py          # Unix/Linux

or

C:>python script.py         # Windows/DOS
```

### 3、IDE：Integrated Development Environment : PyCharm

PyCharm is a Python IDE built by JetBrains, supporting macOS, Windows, and Linux.

PyCharm features : debugging, syntax highlighting, project management, code jumping, smart hints, autocompletion, unit testing, version control ......

PyCharm download address : https://www.jetbrains.com/pycharm/download/

PyCharm installation address: [http://www.runoob.com/w3cnote/pycharm-windows-install.html](https://www.runoob.com/w3cnote/pycharm-windows-install. html)

Professional (Professional Edition, paid): full functionality, 30-day trial.

Community (free): a neutered version of Professional.

![Snipaste_2023-10-03_12-21-10](https://cdn.jsdelivr.net/gh/KXHH2021/yyyyn@mian/img/202310031221858.png)