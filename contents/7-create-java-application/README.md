# 7. Create Java Application

## init task

- best case to use this method is when you have new empty project and you want to generate the necessary Gradle build files quickly and easily. 

Project structure of Java application (`type of project: 2: application`, `implementation language: 3: Java`):
```
├── gradle 
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradlew 
├── gradlew.bat 
├── settings.gradle 
└── app
    ├── build.gradle 
    └── src
        ├── main
        │   └── java 
        │       └── demo
        │           └── App.java
        └── test
            └── java 
                └── demo
                    └── AppTest.java
```
What’s new compared to basic type?
directory `app`. `build.gradle` file moved to `app` directory, as it is now our subproject
`main` directory - default Java source folder
`test` directory - default Java test source folder


## Manually adding Gradle

If you already have code, you can “add” Gradle using terminal.
We have the following structure in project directory `java-app`:
```
   └── src
        └── main
            └── java 
                └── demo
                    └── Hello.java

```
`src/main/java` is a default[^1] Gradle location for Java source code. `demo` is our package.
 
NOTE: you can change source code location, specifying it in `build.gradle` file using `sourceSets` method included into `java` plugin. 

Inside of `Hello.java` is the following:

```
package demo;

public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello!");
    }
}
```
Now what do we need to make this a Gradle project?
1) install Gradle into your machine
2) add Gradle elements: build script and wrapper. 

**Build script**:
- Being in project’s home directory, create `build.gradle` file:
```
plugins {
    id 'application'
}

application {
    mainClass = 'demo.Hello'
}
```
NOTE: `java` plugin is included into `java-library` and `application` plugins, so it is better to apply either of two depending on the project type.

**Wrapper files**:
If you use `gradle wrapper` command, you will get an error:
```
FAILURE: Build failed with an exception.

* What went wrong:
Task 'wrapper' not found in project ‘:java-app'.
```
To fix this error, you need to create `settings.gradle` file in project’s root directory (you can leave it empty if there is only 1 project). Now repeat `gradle wrapper` command.

What’s else can be done:
- add `test` directory
- define repositories and dependencies

```
   └── src
        └── test
            └── java 
                └── demo
                    └── HelloTest.java

```
HelloTest.java:

```
package demo;

import org.junit.Test;

public class HelloTest {
    @Test
    public void verifyNoExceptionThrown() {
        Hello.main(new String[]{});
    }
}
```
build.gradle:
```
plugins {
    id 'application'
}

application {
    mainClass = 'demo.Hello'
}

repositories {
    mavenCentral()
}

dependencies {
    testImplementation group: 'junit', name: 'junit', version: '4.13.2'
}
```
Now when you used command `./gradlew build`, it also executes test. 
Test report -> `build/reports/tests/test`, open `index.html` file.

# !!!!!!!!
(Paste this as screenshot file:///Users/bubblerose/IdeaProjects/java-test/build/reports/tests/test/index.html)

### Additional reading:
- [More about good practices to organise projects](https://docs.gradle.org/current/userguide/organizing_gradle_projects.html)

## Use IDEs

**Create new project**:

Android Studio has built-in support for importing and building Gradle projects.

Eclipse tutorials:
- https://www.vogella.com/tutorials/EclipseGradle/article.html 
- https://www.digitalocean.com/community/tutorials/gradle-eclipse-plugin-tutorial

IntelliJ IDEA tutorials: 
- https://www.jetbrains.com/help/idea/getting-started-with-gradle.html
- https://www.geeksforgeeks.org/how-to-create-a-gradle-project-in-intellij-idea/

**Or add Gradle to existing project in IDE**

If you are already working on some project using IDE of your choice, you can still convert your project to Gradle project. For example:
- [IntelliJ IDEA](https://www.jetbrains.com/help/idea/gradle.html#convert_project_to_gradle)
- [Eclipse](https://www.vogella.com/tutorials/EclipseGradle/article.html#add-gradle-support-to-existing-eclipse-project)

[1^]: Default layout: src vs build, main vs test, java vs resources
- `src` directory is where you keep your source code, tests and resources
- `build` directory contains build output and doesn’t get committed into version control

- `main` - for source code
- `test` - for tests

- `java` for the packages and java classes (`main` or `test`)
- `resources` for files that were created before runtime, so that they can be accessed during runtime

```
src/main/java ->  build/classes/java/main
src/main/resources -> build/resources/main
src/test/java -> build/classes/java/test
src/test/resources -> build/resources/test
```
Layout can be configured and changed, but it is recommended to use the default one.

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md) :arrow_right:|
| --- | --- | --- |
