# 3. Gradle Overview
> open-source build and automation system with an Apache Groovy-based domain specific language (DSL) combining features of Apache Ant and Apache Maven with additional features like a reliable incremental build

## Features
<sub>[Full list](https://gradle.org/features/)</sub>

1. **Faster performance:**
   - incremental builds (if nothing has changed - no need to run the task one more time as it is considered up-to-date)
   - build cache (no need for repeated execution, if it was executed already and there is cache)

2. **Build scans:**
create, customise and share web-based build scans to get full information on build

3. **Customise execution:** 
what tasks will run automatically, excluded, executed even after the failure, etc.

4. **Groovy and Kotlin DSL** to write build scripts

5. **Init plugin** to create new project using setup menu

6. **Dependency management:**
   - automatically downloading dependencies
   - managing configurations (runtime only, compile only dependency, etc)
   - storing dependency cache, etc

7. **Gradle Wrapper**:
   - run build without manual Gradle installation 
   - keep the Gradle version consistent

8. **Packaging and distribution** in JARs, WARs, EARs with build-in tools

9. **Automated testing**

## Gradle core concepts 
Gradle is an open-source customisable build automation tool.
Every Gradle build contains one or more **projects**. 
Each project has one or more **tasks**.

- **Project** - is the thing that Gradle builds (eg.: library JAR, web application).
- **Task** - some piece of work (eg.: compile classes, create JAR, generate Javadoc, publish to repository, run an application).

You can either define the task yourself, or apply a **plugin** (simply: collection of **tasks** and other configurations).
All tasks, dependencies, plugins and configurations are defined in **build scripts**, which Gradle uses to do the job you need him to do. 

**Project** is described and configured by **build script** - a file located in the project’s root directory. 
A single **build** can contain one or more projects and each project can contain their own subprojects. 

A **build** is an execution of a collection of tasks in a Gradle project. You run a build via the command line interface (CLI) or an IDE by specifying task selectors. Gradle configures the build and selects the tasks to run. 

## Build Lifecycle

1. **Initialisation** - determines which projects are going to take part in the build. It is done with help of setting file `settings.gradle`
2. **Configuration** - the build scripts of all projects, which are the part of the build, are executed.
3. **Execution** - Gradle determines the subset of the tasks, created and configured during the configuration phase, to be executed. Gradle then executes each of the selected tasks (depending on working directory and which argument (task name) was passed to `gradle` command)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/4-gradle-project/README.md) :arrow_right:|
| --- | --- | --- |
