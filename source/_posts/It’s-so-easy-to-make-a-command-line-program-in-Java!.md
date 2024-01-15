---
title: It’s so easy to make a command line program in Java!
categories:
  - java
tags:
  - java
description: java simple tutorial
cover: >-
  https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202311221828836.png
abbrlink: 63257
date: 2023-11-22 18:26:45
---

Picocli is the most complete and easiest-to-use command line development framework in Java that I personally think can help everyone quickly develop command line tools.

There are very few tutorials about the Picocli framework on the Internet. The most recommended way to get started is to read the official documentation in addition to the tutorials on Fish Skin.

Official documentation: https://picocli.info/

It is recommended to start with the official quick start tutorial: https://picocli.info/quick-guide.html

Generally, our steps for learning new technologies are: first run through the introductory demo, and then learn the usage and features of the technology.

## Getting started demo

1) Introduce the picocli dependency into the `pom.xml` file of the Maven project:

   ```
   <!-- https://picocli.info -->
   <dependency>
       <groupId>info.picocli</groupId>
       <artifactId>picocli</artifactId>
       <version>4.7.5</version>
   </dependency>
   ```

   

Then we create a new cli.example package under the com.yupi package to store all sample codes related to getting started with Picocli.

2) Copy the example code in the official quick start tutorial to the `com.yupi.cli.example` package, and slightly modify the code in the run method to print the values of the parameters.

```
package com.yupi.cli.example;

import picocli.CommandLine;
import picocli.CommandLine.Command;
import picocli.CommandLine.Option;
import picocli.CommandLine.Parameters;

@Command(name = "ASCIIArt", version = "ASCIIArt 1.0", mixinStandardHelpOptions = true) 
public class ASCIIArt implements Runnable { 

    @Option(names = { "-s", "--font-size" }, description = "Font size") 
    int fontSize = 19;

    @Parameters(paramLabel = "<word>", defaultValue = "Hello, picocli", 
               description = "Words to be translated into ASCII art.")
    private String[] words = { "Hello,", "picocli" }; 

    @Override
    public void run() {
        // 自己实现业务逻辑
        System.out.println("fontSize = " + fontSize);
        System.out.println("words = " + String.join(",", words));
    }

    public static void main(String[] args) {
        int exitCode = new CommandLine(new ASCIIArt()).execute(args); 
        System.exit(exitCode); 
    }
}
```



1. Create a class that implements the `Runnable` or `Callable` interface, which is a command.
2. Mark the class with the `@Command` annotation and name it, and set the `mixinStandardHelpOptions` attribute to true to automatically add `--help` and `--version` options to the application.
3. Set the field as a command line option through the `@Option` annotation. You can set a name and description for the option.
4. Set the field as a command line parameter through the `@Parameters` annotation, and you can specify the default value, description and other information.
5. Picocli will convert the command line parameters into strongly typed values and automatically inject them into the annotation fields.
6. Define business logic in the `run` or `call` method of the class, which will be called when the command is parsed successfully (the user hits Enter).
7. In the `main` method, the command input by the user is processed through the `execute` method of the `CommandLine` object, and the rest is left to the Picocli framework to parse the command and execute the business logic~
8. The `CommandLine.execute` method returns an exit code. You can call `System.exit` with this exit code as a parameter to indicate success or failure to the calling process.



Through this introductory demo, we can briefly summarize the development process of a command:

1. Create a command
2. Set options and parameters
3. Write business logic for command execution
4. Accept input and execute commands through the CommandLine object

After running through the introductory demo, let's learn some practical functions of the Picocli development command line.