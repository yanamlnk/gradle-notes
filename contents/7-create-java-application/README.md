# 7. Create Java Application

## init task

- best case to use this method is when you have new empty project and you want to generate the necessary Gradle build files quickly and easily 

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
- directory `app`. `build.gradle` file moved to `app` directory, as it is now our subproject
- `main` directory - default Java source folder
- `test` directory - default Java test source folder

Once you build your application, new directory will be created called `build`, which also has its own default layout.

### Default layout:

**src vs build**
|`src`|`build`|
|---|---|
|source code, tests and resources|build output *(doesn’t get committed into version control)*|

**main vs test**
|`main`|`test`|
|---|---|
|source code|tests|

**java vs resources**
|`java` |`resources`|
|---|---|
|packages and java classes (`main` or `test`)|files that were created before runtime, so that they can be accessed during runtime|

```
src/main/java ->  build/classes/java/main
src/main/resources -> build/resources/main
src/test/java -> build/classes/java/test
src/test/resources -> build/resources/test
```
Layout can be configured and changed, but it is recommended to use the default one.

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
`src/main/java` is a default Gradle location for Java source code. `demo` is our package.
 
<sub>You can change default source code location, specifying it in `build.gradle` file using `sourceSets` method included into `java` plugin.</sub> 

Inside of `Hello.java` is the following:

```
package demo;

public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello!");
    }
}
```
**Now what do we need to make this a Gradle project?**
1) install Gradle into your machine
2) add Gradle elements: build script and Wrapper. 

**_Build script_**:
- being in project’s home directory, create `build.gradle` file:
```
plugins {
    id 'application'
}

application {
    mainClass = 'demo.Hello'
}
```
<sub>NOTE: `java` plugin is included into `java-library` and `application` plugins, so it is better to apply either of two depending on the project type.</sub>

**_Wrapper files_**:

- if you use `gradle wrapper` command, you will get an error:
```
FAILURE: Build failed with an exception.

* What went wrong:
Task 'wrapper' not found in project ‘:java-app'.
```
To fix this error, you need to create `settings.gradle` file in project’s root directory (you can leave it empty if there is only 1 project). Now repeat `gradle wrapper` command.

**What else can be done:**
- add `test` directory
- define repositories and dependencies

```
   └── src
       ├── main
       │     └── (...)
       └── test
            └── java 
                └── demo
                    └── HelloTest.java
```
`HelloTest.java`:

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
`build.gradle`:
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
Now when you use command `./gradlew build`, it also executes test. 

**Test report** -> `build/reports/tests/test`, open `index.html` file.

<img width="936" alt="image" src="https://user-images.githubusercontent.com/90959658/211142895-a6edafed-b810-4574-9646-ce892da15a6f.png">

### Additional reading:
- [More about good practices to organise projects](https://docs.gradle.org/current/userguide/organizing_gradle_projects.html)

## Use IDEs

**Create new project**:

- **_Android Studio_** has built-in support for importing and building Gradle projects.
- **_Eclipse tutorials_**:
  - [Using the Gradle build system in the Eclipse IDE - Tutorial](https://www.vogella.com/tutorials/EclipseGradle/article.html)
  - [Gradle Eclipse Plugin Tutorial](https://www.digitalocean.com/community/tutorials/gradle-eclipse-plugin-tutorial)
- **_IntelliJ IDEA tutorials_**: 
  - [Getting Started with Gradle](https://www.jetbrains.com/help/idea/getting-started-with-gradle.html)
  - [How to Create a Gradle Project in IntelliJ IDEA?](https://www.geeksforgeeks.org/how-to-create-a-gradle-project-in-intellij-idea/)

**Or add Gradle to the existing project in IDE**:
- If you are already working on some project using IDE of your choice, you can still convert your project to Gradle project. For example:
  - [IntelliJ IDEA](https://www.jetbrains.com/help/idea/gradle.html#convert_project_to_gradle)
  - [Eclipse](https://www.vogella.com/tutorials/EclipseGradle/article.html#add-gradle-support-to-existing-eclipse-project)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md) :arrow_right:|
| --- | --- | --- |
