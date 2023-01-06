# 4. Gradle Project

## Basic project using gradle init command

1. Create a directory of your project and go to it.
```
mkdir gradle-tutorial
cd gradle-tutorial 
```
2. Use command `gradle init`. You will see a menu you can choose from. Each question has its default values. For this project choose: 
    - type `1: basic`
    - build script DSL `1: Groovy`
    - project name may be default (= directory name). *Just hit `Enter` to choose default*

```
BUILD SUCCESSFUL in 15s
2 actionable tasks: 2 executed
```

## Basic structure

After you used command `gradle init`, the project is created with the following structure:

```
.
├── build.gradle
├── gradle 
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradlew 
├── gradlew.bat 
└── settings.gradle 

```

1. `build.gradle` is a build script that Gradle uses to configure project. Here you can define tasks, plugins, dependencies and other configurations. More about it in [Build Script](https://github.com/yanamlnk/gradle-notes/tree/main/contents/5-build-script) section.

2. Gradle Wrapper files: 
    - `gradle-wrapper.jar` - contains code for downloading the Gradle distribution
    - `gradle-wrapper.properties` - responsible for configuring the Wrapper runtime behavior e.g. the Gradle version compatible with this version
    - `gradlew` and `gradlew.bat` - a shell script and a Windows batch script for executing the build with the Wrapper

Gradle Wrapper is explained in [Wrapper](https://github.com/yanamlnk/gradle-notes/tree/main/contents/6-gradle-wrapper) section. Shortly speaking, it’s a script that executes tasks using previously declared Gradle version without required manual installation.

3. `settings.gradle` file specifies which projects to include in your build. Optional for single project build (mandatory for multi-project build). 

Example of file content for simple Java application build:
```
rootProject.name = 'demo'
include('app')
```

- `rootProject.name` - name of the build, which overrides the default behaviour of naming the build after the directory it’s in. It’s recommended to set a fixed name as the folder might change if the project is shared.
- `include('app')` defines that the build consists of one subproject called `app` that contains the actual code and build logic. More subprojects can be added by additional `include(...)` statements.

4. `.gradle` is a hidden directory with project-specific cache used internally by Gradle.
5. `.gitignore` file is created automatically and by default contains the following:

```
# Ignore Gradle project-specific cache directory
.gradle

# Ignore Gradle build output directory
build
```
6. `.gitattributes` is one more hidden file which contains Git settings for files and paths attributes that should be used by git when performing git actions.

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md) :arrow_right:|
| --- | --- | --- |
