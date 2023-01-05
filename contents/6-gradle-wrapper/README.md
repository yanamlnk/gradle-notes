# 6. Gradle Wrapper
*gradlew = gradle + w(rapper)*

## Executing tasks

`./gradlew taskName` - Linux/Mac
`./gradlew.bat taskName` - Windows
`./` - if you are currently in project root directory

If no taskName specified, and there are no default tasks in `build.gradle` file, task `help` will be executed.

## Wrapper overview

- Wrapper is a script used to invoke Gradle and run tasks
- contains Gradle version originally used for project creation
- always run/build using Wrapper commands (to avoid incompatibility issues caused by different versions)
- but NOT when you are initialising new Gradle project. `gradlew(.bat)` works only if you already have Wrapper files added to the project
- can be used to run/build Gradle project without local installation (since Wrapper script contains info on Gradle version used for project, it will automatically download the specified version and cache it in the `.gradle/wrapper/dists` directory in your user home directory to avoid downloading it every time)
- all Wrapper files should be checked into version control to let the others run the project without the need to install Gradle

## gradle vs gradlew

`gradle`: 
- initialise a new project as a Gradle project
- generate the Gradle wrapper
`gradlew`:
- build a project
- test a project
- run any other Gradle task in a project

## Add Wrapper to the project

1) run command `gradle init` in project directory to create new project using setup menu - Wrapper files will be automatically added to the project directory
2) OR command `gradle wrapper` in project directory to add Wrapper files manually

- Wrapper should be added to the project only once. There is no need to generate new files when you just want to update Gradle version.

## Upgrade version of Gradle using Wrapper

- by default, `init` and `wrapper` tasks will use the version of Gradle installed on your machine

Check version with command `./gradlew --version` 
```
------------------------------------------------------------
Gradle 7.5.1
------------------------------------------------------------
```
or by checking `gradle-wrapper.properties` file (`distributionUrl` info): 

**gradle/wrapper/gradle-wrapper.properties** 
```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-7.5.1-bin.zip
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists

```

To upgrade version, run command `./gradlew wrapper --gradle-version=<version>`, eg.:
```
./gradlew wrapper --gradle-version=7.6
```
Next time you use Wrapper (any task), the new version will be downloaded. 

You can also specify distribution type:
```
./gradlew wrapper --gradle-version=7.6 --distribution-type=bin
```
Available options are `bin` and `all`. The default value is `bin`.
`bin` - for binary distribution containing only the runtime, `all` - binary + sources + documentation

You can also upgrade by generation distribution URL and manually changing the property in `gradle-wrapper.properties` file.
```
distributionUrl=https\://services.gradle.org/distributions/gradle-7.6-all.zip
```
**Do not forget to commit changes to the Wrapper files to version control.**

- `wrapper` task only updates `gradle-wrapper.properties` file with new version. Usually it does not cause any troubles in execution, but if you want to update `gradle-wrapper.jar`, too, run `wrapper` task for the second time.

You can customise the Wrapper task in `build.gradle` file. For example, change default distribution type from `bin` to `all`:
```
tasks.named('wrapper') {
    distributionType = Wrapper.DistributionType.ALL
}
```
### Additional reading:
- [Verify the integrity of Wrapper JAR file to avoid potentially dangerous file](https://docs.gradle.org/current/userguide/gradle_wrapper.html#wrapper_checksum_verification)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md) :arrow_right:|
| --- | --- | --- |
