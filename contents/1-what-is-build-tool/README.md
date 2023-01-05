# 1. What is Build Tool?

## How do you “build” your code? 
``` 
	         Compile (transform
	         into .class file)                            Run
Source code ------------------------------> Bytecode -----------------------> JVM
(Your code in                             (1s and 0s)	     	     (Java Virtual Machine
 .java file)	   						       takes bytecode and 
									   runs it)
``` 				

## How do you compile and run your code?

1. JDK (Java Development Kit) has a compiler command `javac`. Run in terminal:

```
javac Program.java
```
Program.class file will be created. To run it: use `java` command. If you are on the same directory as your source code, then:
```
java -cp . Program
```
2. IDE of your choosing usually has its own build mechanism.

## Why do you need to use separate build tool?

`javac` is great for small programs with few classes, but when your application uses 3rd party libraries (in jar files) (and you will use them a lot), things got complicated and time-consuming. 
```
javac -cp lib1.jar;lib2.jar;lib3.jar MyProgram.java
```
Build mechanism in IDE is great, but mostly pretty simple compared to build tools. With it you can’t:
- set up custom/complex build configurations
- download and add dependencies
- run tests
- package compiled code

## What build tools for Java exist?

Most popular are:
1. Apache Ant - the oldest
2. Apache Maven - the most popular
3. Gradle - the newest

Apache Maven and Gradle are more than simply build tools. They manage almost the entire lifecycle of an application.

### Additional reading: 
- [Difference between Gradle and Maven](https://www.geeksforgeeks.org/difference-between-gradle-and-maven/)
- [How to migrate to Gradle from Maven](https://docs.gradle.org/current/userguide/migrating_from_maven.html#migrating_from_maven)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md) :arrow_right:|
| --- | --- | --- |
