# 8. Work with Gradle

## Command-line interface

:grey_exclamation: to use wrapper, substitute `./gradlew` or `gradlew.bat` for `gradle` :grey_exclamation:

**Execute task**:
```
gradle [taskName...] [--option-name...]
``` 
- Multiple tasks should be separated with a space
- Options that accept values can be specified with or without `=`, however, use of `=` is recommended
```
--console=plain

```
- Options that enable behaviour have opposites with `--no-`
```
--build-cache
--no-build-cache
```
- Many long-form options, have short option equivalents:
```
--help
-h
```
- Execute task in a multi-project build:
```
gradle :my-subproject:taskName
gradle my-subproject:taskName

```
- When invoking Gradle from within a subproject, the project name should be omitted:
```
cd my-subproject
gradle taskName
```
no need to type full task name, only the part that will uniquely distinguish from other tasks:
```
gradle che == gradle check

gradle  mAL:cT == gradle my-awesome-library:compileTest
```

**Common tasks**:
`gradle init` - initialises a new Gradle build

`gradle tasks` - gives list of the main tasks
`gradle tasks --all` - gives more information on available tasks
`gradle help --task someTask` - gives detailed information about a specific task
`gradle --help` - gives a list of command-line options

`gradle build` - assembles all outputs and runs all checks.
`gradle run` - assembles the application and executes some script or binary
`gradle check` - executes all verification tasks, including tests and linting
`gradle clean` - deletes the contents of the build directory

## Gradle & Third-party Tools

[IDEs](https://docs.gradle.org/current/userguide/third_party_integration.html#ides):
- Android Studio
- Eclipse
- IntelliJ IDEA
- NetBeans
- Visual Studio
- Xcode
- CLion

[CI platforms](https://docs.gradle.org/current/userguide/third_party_integration.html#continuous_integration)
- Jenkins
- TeamCity
- Travis CI

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md) :arrow_right:|
| --- | --- | --- |
