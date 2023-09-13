# Gradle Notes

## Intro
These notes were created solely for educational purposes while I was learning Gradle on my own.
The main focus is to grasp Gradle basics, terminology, concepts and workflow. That is why for simplicity I am using:
- `Groovy` as build script language
- `Java` as main programming language
- `zsh` in Terminal

## Where to start?

### :grey_exclamation: Click [here](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md) to start :grey_exclamation:

:wavy_dash: *or feel free to jump to any topic, using **Table of Contents** below* :wavy_dash:

### Interested in Maven? :eyes: 
Check new bonus chapter: :feather: [Maven Notes](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md) :feather:

## Table of Contents:
1. [What is Build Tool?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md)
<details><summary><sub>Learn how to "build" your project, what built-in options do you have, and why do you need build tools.</sub></summary>
<p>

  - [How do you “build” your code?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md#how-do-you-build-your-code)
  - [How do you compile and run your code?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md#how-do-you-compile-and-run-your-code)
  - [Why do you need to use separate build tool?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md#why-do-you-need-to-use-separate-build-tool)
  - [What build tools for Java exist?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md#what-build-tools-for-java-exist)

</p>
</details>

2. [How to Install?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md)
<details><summary><sub>Prerequisites, installation.</sub></summary>
<p>

  - [Prerequisites](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md#prerequisites)
  - [Installation](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md#installation)
  - [How to check that Gradle is installed?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md#how-to-check-that-gradle-is-installed)
  - [When you don’t need installation?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/2-how-to-install/README.md#when-you-dont-need-installation)

</p>
</details>

3. [Gradle Overview](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md)
<details><summary><sub>Learn about Gradle features, core concept, and what lifecycle Gradle build has.</sub></summary>
<p>

  - [Features](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md#features)
  - [Gradle core concepts](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md#gradle-core-concepts)
  - [Build Lifecycle](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md#build-lifecycle)

</p>
</details>

4. [Gradle Project](https://github.com/yanamlnk/gradle-notes/blob/main/contents/4-gradle-project/README.md)
<details><summary><sub>Learn how to create basic Gradle project, and what structure it has.</sub></summary>
<p>

  - [Basic project using gradle init command](https://github.com/yanamlnk/gradle-notes/blob/main/contents/4-gradle-project/README.md#basic-project-using-gradle-init-command)
  - [Basic structure](https://github.com/yanamlnk/gradle-notes/blob/main/contents/4-gradle-project/README.md#basic-structure)

</p>
</details>

5. [Build Script](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md)
<details><summary><sub>Learn how to configure Gradle build using build script, get to know basic build.gradle structure, and also some Groovy basics - Gradle DSL.</sub></summary>
<p>

  - [build.gradle(.kts)](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#buildgradlekts)
    - [What can be added to the file?](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#what-can-be-added-to-the-file)
    - [plugins](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#plugins)
    - [metadata](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#metadata)
    - [repositories](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#repositories)
    - [dependencies](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#dependencies)
    - [tasks](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#tasks)
  - [Groovy basics](https://github.com/yanamlnk/gradle-notes/blob/main/contents/5-build-script/README.md#groovy-basics)

</p>
</details>

6. [Gradle Wrapper](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md)
<details><summary><sub>Learn what is Gradle Wrapper, why it is so useful, and how to use/upgrade it.</sub></summary>
<p>

  - [Executing tasks](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md#executing-tasks)
  - [Wrapper overview](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md#wrapper-overview)
  - [gradle vs gradlew](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md#gradle-vs-gradlew)
  - [Add Wrapper to the project](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md#add-wrapper-to-the-project)
  - [Upgrade version of Gradle using Wrapper](https://github.com/yanamlnk/gradle-notes/blob/main/contents/6-gradle-wrapper/README.md#upgrade-version-of-gradle-using-wrapper)

</p>
</details>

7. [Create Java Application](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md)
<details><summary><sub>Create simple Java application using different methods: init task, IDEs, or manually add Gradle to the project.</sub></summary>
<p>

  - [init task](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md#init-task)
  - [Manually adding Gradle](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md#manually-adding-gradle)
  - [Use IDEs](https://github.com/yanamlnk/gradle-notes/blob/main/contents/7-create-java-application/README.md#use-ides)

</p>
</details>

8. [Work with Gradle](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md)
<details><summary><sub>Work with Gradle using CLI or third-party tools.</sub></summary>
<p>

  - [Command-line interface](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md#command-line-interface)
  - [Gradle & Supported Third-party Tools](https://github.com/yanamlnk/gradle-notes/blob/main/contents/8-work-with-gradle/README.md#gradle--supported-third-party-tools)

</p>
</details>

9. [Share Project](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md)
<details><summary><sub>Learn where Gradle stores build output, how to generate build artifacts: jar, tar or zip files, and how to publish your library.</sub></summary>
<p>

  - [build directory](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md#build-directory)
  - [Generate jar](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md#generate-jar)
  - [Distribute application](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md#distribute-application)
  - [Publish](https://github.com/yanamlnk/gradle-notes/blob/main/contents/9-share-project/README.md#publish)

</p>
</details>

10. [Multi-Project Build](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md)
<details><summary><sub>Learn about multi-project build structure, how to execute tasks, and how subprojects can depend on each other.</sub></summary>
<p>
  
  - [Structure](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md#structure)
  - [Declare dependencies between subprojects](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md#declare-dependencies-between-subprojects)
  - [Execute tasks](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md#execute-tasks)
  - [Sharing common configurations](https://github.com/yanamlnk/gradle-notes/blob/main/contents/10-multi-project-build/README.md#sharing-common-configurations)

</p>
</details>

11. [Troubleshooting Gradle](https://github.com/yanamlnk/gradle-notes/blob/main/contents/11-troubleshooting-gradle/README.md)
<details><summary><sub>Learn where you can ask for help in case of some Gradle issues, and what is Build Scan.</sub></summary>
<p>

  - [Places to ask](https://github.com/yanamlnk/gradle-notes/blob/main/contents/11-troubleshooting-gradle/README.md#places-to-ask)
  - [Troubleshooting docs](https://github.com/yanamlnk/gradle-notes/blob/main/contents/11-troubleshooting-gradle/README.md#troubleshooting-docs)
  - [Publish and share Build Scan](https://github.com/yanamlnk/gradle-notes/blob/main/contents/11-troubleshooting-gradle/README.md#publish-and-share-build-scan)

</p>
</details>

12. [Maven Notes](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md)
<details><summary><sub>Learn how to use Maven and what are the differences and similarities between Gradle and Maven functionality.</sub></summary>
<p>
  
  - [Install Maven](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#install-maven)
  - [What is Maven](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#what-is-maven)
  - [Gradle vs Maven](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#gradle-vs-maven)
    - [Short overview](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#short-overview)
    - [Maven project creation](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#maven-project-creation)
    - [IDE support](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#ide-support)
    - [Project structure](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#project-structure)
    - [Configuration (pom.xml)](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#configuration)
    - [Commands to work with the tool](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#commands-to-work-with-the-tool)
    - [Plugins](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#plugins)
    - [Multi-project](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#multi-project)
    - [Build output files](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#build-output-files)
    - [Maven Wrapper](https://github.com/yanamlnk/gradle-notes/blob/main/contents/12-maven-notes/README.md#maven-wrapper)

</p>
</details>

13. [Resources](https://github.com/yanamlnk/gradle-notes/blob/main/resources/README.md)
    
<sub>Links to the resources that were used to write these cheatsheets.</sub>

