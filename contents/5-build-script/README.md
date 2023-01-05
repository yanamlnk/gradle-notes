# 5. Build Script

## build.gradle(.kts)

build script (although strictly speaking it is a build configuration script), that Gradle uses to configure and build projects. It defines a project and its tasks.
each project has build.gradle file (in multi-project builds each project has its own file)
can be written in Groovy (`build.gradle`) or Kotlin (`build.gradle.kts`)
you run a Gradle build using the `gradle` command. The `gradle` command looks for a file called `build.gradle(.kts)` in the current directory

### What can be added to the file?

**build.gradle** example in Groovy for Java application:

```
plugins {
    id 'application' // 1
}

group 'org.example'
version '1.0-SNAPSHOT' // 2

repositories {
    mavenCentral() // 3
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.1' // 4

    implementation 'com.google.guava:guava:31.1-jre' // 5
}

application {
    mainClass = 'demo.App' // 6
}

tasks.named('test') {
    useJUnitPlatform() 
}
```

`1`: Apply the **application plugin** to add support for building a CLI application in Java
`2`: Build metadata: project’s **group and version**
`3`: Use Maven Central for **resolving dependencies**
`4`: Use JUnit Jupiter for **testing**
`5`: This dependency is used by the application
`6`: Define the main class for the application (configure `application` plugin)

### plugins

extend the capabilities of the project by automatically adding new tasks
no limit of the maximum number of plugins used in a project
almost all Gradle functionality is covered by core or 3rd party plugins

Plugin library:
[Core plugins](https://docs.gradle.org/current/userguide/plugin_reference.html)
[Community-made plugins](https://plugins.gradle.org)

Apply core plugin called `application`:

```
plugins {
    id 'application'
}
```

Plugins allow additional configurations. For `application` plugin we can specify main class:

```
application {
    mainClass = 'demo.App'
}
```

### metadata

Information about your build that can be used, for example, for naming build .jar artifact.

```
group 'org.example'
version '1.0-SNAPSHOT'
```

### repositories

repository is a location from which dependencies will be downloaded and added to the project

Supported types:
public repositories like Maven Central and Google
custom repositories by URL (Maven or Ivy compatible)
local (flat) directories (download the jar and place it in your project, commonly in the `libs` folder of your project - useful when jar you need is not in public repository)


```
repositories {

// public repository
    mavenCentral()

// repository by URL
    maven {
        url "https://repo.spring.io/release"
    }

// local (flat) directories
    flatDir {
        dirs 'lib1', 'lib2'
    }

}
```

### dependencies

dependencies are used to add external libraries to the project
Gradle will automatically download them from repositories and put them in the archive with the application

Each dependency has **configuration**. Most of the configurations come with core plugins (for example with `java` plugin).

Why do you need configurations?
- to categorise and declare dependencies based on their purposes (eg.: compile/runtime/both) during the execution of the tasks (eg. Spring web framework dependency to compile the source code)

Most popular configurations:
- implementation - compile + runtime classpaths (*default*)
- compileOnly - compile
- runtimeOnly - runtime

Tests have different dependencies, since they are compiled and run separately and are not included in the final jar file (as well as their dependencies) to decrease the size of jar.
- testImplementation
- testCompileOnly
- testRuntimeOnly

<sub>Usually type of configuration is already mentioned in repository[^1].</sub>


**Declaring dependency**
Define the following attributes of the dependency: 
- group
- name (artifactId)
- version 
*Flat repository only needs a name and a version.*

There are different ways in syntax to do it:

```
dependencies {
    runtimeOnly group: 'org.springframework', name: 'spring-core', version: ‘2.5'

    runtimeOnly 'org.springframework:spring-core:2.5',
            ‘org.springframework:spring-aop:2.5'

    runtimeOnly(
        [group: 'org.springframework', name: 'spring-core', version: '2.5'],
        [group: 'org.springframework', name: 'spring-aop', version: '2.5']
    )

    runtimeOnly('org.hibernate:hibernate:3.0.5') {
        transitive = true
    }

    runtimeOnly group: 'org.hibernate', name: 'hibernate', version: '3.0.5', transitive: true

    runtimeOnly(group: 'org.hibernate', name: 'hibernate', version: '3.0.5') {
        transitive = true
    }
}

```
Dependencies can have their own dependencies. These additional dependencies called [transitive](https://docs.gradle.org/current/userguide/dependency_management_terminology.html#sub:terminology_transitive_dependency).

*(After you declared dependencies, don’t forget to `import` them into your code)*

**More about version:** 
- `2.3` - 2.3 or later (if there is a conflict - highest version will be chosen)
- `2.3!!` - strictly 2.3
- `2.+` - latest 2.+ version —> **dynamic version** (version may change to the latest one, 2.+ may be 2.6 one day, and 2.7 the other)
- `2.7-SNAPSHOT` - SNAPSHOT of 2.7 —> **changing version** (artifacts for the same version may update)

*By default, dynamic and changing version are cached for 24 hours (can be configured)*

Documenting a dependency:
```
dependencies {
    implementation('org.ow2.asm:asm:7.1') {
        because 'we require a JDK 9 compatible bytecode generator'
    }
}
```
View dependencies of a subproject: `gradle dependencies`

### tasks

Categories: 
- built-in (init, wrapper)
- provided by plugins (compile, test)
- custom (locally defined)

Execute task (-q is optional[^2]):
```
gradle -q name_of_task
```

View tasks of the project:
```
gradle tasks	     // to view basic tasks
gradle tasks --all  // to view additional
```

Tasks belong to project. Different projects can have different tasks.

Example:
```
tasks.register('hello') {
    doLast {
        println 'Hello world!'
    }
}
```
Command: `gradle -q hello`
Output: `Hello world!`

Tasks can depend on other tasks and form task graphs[^3] (task trees):

```
tasks.register('hello') {
    doLast {
        println 'Hello world!'
    }
}
tasks.register('intro') {
    dependsOn tasks.hello
    doLast {
        println "I'm Gradle"
    }
}
```
Command: `gradle -q intro`
Output: `Hello world!`
`I'm Gradle`

Define default tasks:

```
defaultTasks 'clean', 'run'

tasks.register('clean') {
    doLast {
        println 'Default Cleaning!'
    }
}

tasks.register('run') {
    doLast {
        println 'Default Running!'
    }
}

tasks.register('other') {
    doLast {
        println "I'm not a default task!"
    }
}
```
Command: `gradle -q`
Output: `Default Cleaning!`
`Default Running!`

Command: `gradle -q other`
Output: `I'm not a default task!`

Command: `gradle -q clean`
Output: `Default Cleaning!`

Add description and group to your custom task, so that it will be shown with description using `tasks --all` command:
```
tasks.register('hello') {
    group = "basic"
    description = "task to say hello"
    println 'Hello world!'
}
```

Command: `gradle hello`
Output: `Hello world!`

Command: `gradle tasks --all`
Output:
```
> Task :tasks
Hello world!

(...)

Basic tasks
-----------
hello - task to say hello

Build Setup tasks
-----------------
init - Initializes a new Gradle build.
wrapper - Generates Gradle wrapper files.

(...)
```

### Additional reading:
- [Other build script blocks](https://docs.gradle.org/current/dsl/index.html#N10060)
- [Dependency configurations included by Java plugin](https://docs.gradle.org/current/userguide/java_library_plugin.html#sec:java_library_configurations_graph)
- [Configurations: implementation vs api](https://docs.gradle.org/current/userguide/java_library_plugin.html#sec:java_library_recognizing_dependencies)
- [More about tasks](https://docs.gradle.org/current/userguide/more_about_tasks.html)

## Groovy basics

**Little background first…**
- Gradle provides a domain specific language[^4], or DSL, for describing builds. This build language is available in Groovy and Kotlin.
- As Groovy is an object-oriented language based on Java, its properties and methods apply to objects.
- Each build script is associated with an object of type **Project** and as the build script executes, it configures this **Project**. Almost all top-level properties and blocks in a build script are part of the Project API.

```
version = '1.0.0.GA'

configurations {
    ...
}
```
Both `version` and `configurations {}` are part of `org.gradle.api.Project`. This example reflects how every Groovy build script is backed by an implicit instance of **Project**.

**Now back to Groovy DSL.**
4 key elements:

1) **Properties**
- some state of an object
```
<obj>.<name>                // Get a property value
<obj>.<name> = <value>      // Set a property to a new value
"$<name>"                   // Embed a property value in a string
"${<obj>.<name>}"           // Same as previous (embedded value)
```

```
version = '1.0.1'
myCopyTask.description = 'Copies some files'

file("$buildDir/classes")
println "Destination: ${myCopyTask.destinationDir}"

```

2) **Methods**
- some behavior of an object
- Gradle often uses methods to configure the state of objects as well

```
<obj>.<name>()              // Method call with no arguments
<obj>.<name>(<arg>, <arg>)  // Method call with multiple arguments
<obj>.<name> <arg>, <arg>   // Method call with multiple args (no parentheses)
```

```
myCopyTask.include '**/*.xml', '**/*.properties'

ext.resourceSpec = copySpec() 

file('src/main/java')
println 'Hello, World!'
```

3) **Blocks**
- also methods, just with specific type for the last argument - closure (`{}`)
- configure multiple aspects of build element in one go
- simply speaking, closure is a function as a variable. In other words, it is variable defined in curly brackets `{}`

```
<obj>.<name> {
     ...
}

<obj>.<name>(<arg>, <arg>) {
     ...
}
```

```
plugins {
    id 'java-library'
}

configurations {
    assets
}

sourceSets {
    main {
        java {
            srcDirs = ['src']
        }
    }
}

dependencies {
    implementation project(':util')
}
```

4) **Local variables**

```
def <name> = <value>        // Untyped variable
<type> <name> = <value>     // Typed variable

```
```
def i = 1
String errorMsg = 'Failed, because reasons'

```

- Avoid using local variables in the root of the project, i.e. as pseudo project properties. They cannot be read outside of the build script and Gradle has no knowledge of them
- Within a narrower context — such as configuring a task — local variables can occasionally be helpful

**A bit on syntax**:
you can use `def` keyword instead of providing type
`;` not required
`( )` are optional when passing >=1 parameters to a method. Required when a method has 0 arguments.
`{ }` for defining blocks

<sub>[^1]: Public repositories usually include a declaration of the dependency:</sub>
[Google](https://maven.google.com/web/index.html):
[Maven](https://mvnrepository.com/):

<sub>[^2]: **-q** hides log messages, so that only the output of the tasks is shown. You don’t need to use it if you don’t want to.</sub>

<sub>[^3]: “[Task graph](https://tomgregory.com/all-about-the-gradle-task-graph/) is the structure which is formed from all the dependencies between tasks in a Gradle build.”</sub>

<sub>[^4]: “[A Domain Specific Language](https://www.jetbrains.com/mps/concepts/domain-specific-languages/) is a programming language with a higher level of abstraction optimized for a specific class of problems. A Domain specific language is usually less complex than a general-purpose language, such as Java, C, or Ruby. Generally, DSLs are developed in close coordination with the experts in the field for which the DSL is being designed. In many cases, DSLs are intended to be used not by software people, but instead by non-programmers who are fluent in the domain the DSL addresses.”</sub>

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/4-gradle-project/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md) :arrow_right:|
| --- | --- | --- |
