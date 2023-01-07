# 9. Share Project

## build directory

- `build` directory is located in your project root directory into which Gradle generates all build artifacts (for example, after you use `build` task):
  - compiled classes (`build/classes`)
  - jar file (`build/libs`)
  - project archives (`build/distributions`)
  - test report (`build/reports/tests/test/index.html`)

`build` folder is usually ignored by version control.

<sub>Tests will not be included into final build artifact as they are not required to execute application.</sub>

## Generate jar

- `jar` task, or automatically with `build` task (with `java` plugin applied)
- takes compiled classes and resources from `build` directory and adds them to the **.jar** file
- name of the **.jar** file: `<project-name>-<version>.jar` (name from `settings.gradle`, version from `build.gradle`)
- new file will be in `build/libs` directory
- to avoid `no main manifest attribute`[^1] error when running generated jar file, edit `build.gradle` file beforehand:

```
jar {
    manifest {
        attributes “Main-Class": “fullClassName”
    }
}
```
*fullClassName: package + name of the main class without .java extension.*
```
   └── src
        └── main
            └── java 
                └── demo
                    └── Hello.java
```
Then fullClassName = “demo.Hello”

- To run the program using jar file, use the command `java -jar pathToJarFile/nameOfJarFile`

## Distribute application 

After command `gradle build`, or `gradle assemble`, Gradle will produce the archives in 2 formats (.tar and .zip) located in `build/distributions` directory.

## Publish

1) define what to publish (combination of artifacts and metadata) - `publications`
2) define where to publish (to which repository) - `repositories`
3) do the publishing (Gradle automatically generates publishing tasks)

<sub>Each of these steps is dependent on the type of the repository to which you want to publish artifacts (e.g. Maven or Ivy repositories).</sub>

1) apply appropriate publishing plugin:
    - [Maven Publish Plugin](https://docs.gradle.org/current/userguide/publishing_maven.html#publishing_maven)
    - [Ivy Publish Plugin](https://docs.gradle.org/current/userguide/publishing_ivy.html#publishing_ivy)

```
plugins {
    id 'java-library'
    id 'maven-publish'
}
```

2) configure `publishing`: `publications` and `repositories`
```
group = 'org.example'
version = '1.0'

publishing {
    publications {
        myLibrary(MavenPublication) {
            from components.java
        }
    }

    repositories {
        maven {
            name = 'myRepo'
            url = layout.buildDirectory.dir("repo")
        }
    }
}
```
- `myLibrary` - name of publication with type `MavenPublication`

- `components.java` - the `java` component in its default setup consists of a JAR — produced by the `jar` task — and the dependency information of the Java api and runtime variants. It may also define additional variants, for example sources and Javadoc, with the corresponding artifacts.

The default Maven POM identifying attributes are:
- groupId - project.group
- artifactId - project.name
- version - project.version

But you can specify these attributes manually:
```
    publications {
        myLibrary(MavenPublication) {
            groupId = 'org.example'
            artifactId = 'sample'
            version = “1.0"
            from components.java
        }
    }
```
- `'myRepo'` is file-based Maven repository.

Basic publishing to an Ivy repository is very similar: you simply use the `Ivy Publish Plugin`, replace `MavenPublication` with `IvyPublication`, and use `ivy` instead of `maven` in the repository definition.
 
3) after you configured publishing, run:
```
gradle publish
```
[^1]: JAR file is essentially a zip file that contains an optional `META-INF` directory. Files/directories in the `META-INF` directory are used to configure applications, extensions, class loaders and services. For example, `MANIFEST.MF` file has an information about version, owner, **main class**, and so on. [More info](https://docs.oracle.com/javase/7/docs/technotes/guides/jar/jar.html#The_META-INF_directory)
#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md) :arrow_right:|
| --- | --- | --- |
