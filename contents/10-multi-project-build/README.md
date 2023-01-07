# 10. Multi-Project Build

## Structure 

- consists of one root project, and one or more subprojects

Example of a multi-project build that contains subprojects called `app` and `lib`:

```
.
├── app
│   ...
│   └── build.gradle
├── lib
│   ...
│   └── build.gradle
└── settings.gradle
```

The root project does not have a Gradle build file, only a settings file that defines the subprojects to include.

```
rootProject.name = 'basic-multiproject'
include 'app'
include 'lib'
```

`include` statement is to tell Gradle to look for a build file for subprojects in the mentioned subdirectories.

- to view the structure: `gradle projects` command
- the type of the subproject is usually defined by plugins applied 

## Declare dependencies between subprojects

- for example, when one subproject needs to use build artifacts from another

Example: declare the dependencies on the `utils` and `api` projects from the `web-service` project in `web-service/build.gradle`:
```
dependencies {
    implementation project(':utils')
    implementation project(':api')
}

//type-safe API since Gradle 7:
dependencies {
    implementation projects.utils
    implementation projects.api
}
```

## Execute tasks

**By name**:
- command `gradle test` will execute the `test` task in any subproject, relative to the current working directory, that have that task
- the basic rule behind Gradle’s behaviour is: execute all tasks down the hierarchy which have this name

**By fully qualified name**: 
- `gradle :services:webservice:build` will run `build` task of the `webservice` subproject, located in `services` project.

## Sharing common configurations

- `buildSrc` - special subproject 

- best practice: use for custom tasks
  - build files -> configurations only 
  - custom tasks -> buildSrc

- great tool for encapsulation as long as the code does not need to be shared among multiple, independent projects
- upon discovery of the directory, Gradle automatically compiles and tests this code and puts it in the classpath of your build script
- for multi-project builds there can be only one `buildSrc` directory, which has to sit in the root project directory

A typical project including `buildSrc` has the following layout. Any code under `buildSrc` should use a package similar to application code. 
```
.
├── buildSrc
│   ├── build.gradle
│   └── src
│       ├── main
│       │   └── java
│       │       └── com
│       │           └── enterprise
│       │               ├── Deploy.java
│       │               └── DeploymentPlugin.java
│       └── test
│           └── java
│               └── com
│                   └── enterprise
│                       └── DeploymentPluginTest.java
├── settings.gradle
├── subprojecto-one
│   └── build.gradle.kts
└── subproject-two
    └── build.gradle.kts
```

Optionally, the `buildSrc` directory can host a build script if additional configuration is needed (e.g. to apply plugins or to declare dependencies). 

`buildSrc` can be used as plugin, which is visible to every build script used by the build. However, it is not visible outside the build, and so you cannot reuse the plugin outside the build it is defined in.
```
├── buildSrc
│   ├── build.gradle
│   ├── src
│   │   ├── main
│   │   │   └── groovy
│   │   │       └── myproject.java-conventions.gradle
│   │   │      

```
Example: `projectB` - public Java library that uses `projectA` as an internal shared library. Both are Java projects, so we can apply common set of rules to them.
**projectA/build.gradle**
```
plugins {
    id 'myproject.java-conventions'
}

dependencies {
    // internal module dependencies
}
```
**projectB/build.gradle**
```
plugins {
    id 'myproject.java-conventions'
}

dependencies {
    implementation project(':projectA')
}
```
<sub>[Check full sample here](https://docs.gradle.org/current/samples/sample_convention_plugins.html).</sub>

:grey_exclamation: A change in `buildSrc` causes the whole project to become out-of-date, so don’t forget to run a full build regularly (with small changes you can use `--no-rebuild` command-line option to get faster feedback) :grey_exclamation:

### Additional reading:
- [How to create software product which consists of several Gradle builds (singe or multi-project)](https://docs.gradle.org/current/userguide/structuring_software_products.html)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/11-troubleshooting-gradle/README.md) :arrow_right:|
| --- | --- | --- |
