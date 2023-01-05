# Gradle Notes

## Intro
These notes were created solely for educational purposes while I was learning Gradle on my own.
The main focus is to grasp Gradle basics, terminology, concepts and workflow. That is why for simplicity I am using:
- Groovy as build script language
- Java as main programming language
- zsh in Terminal

## Where to start?
- If you want to start reading for the beginning, click [here](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md).
- Feel free to jump to any topic you are interested in, using table of contents below.

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

2. [How to Install?]()
<details><summary><sub>Prerequisites, installation.</sub></summary>
<p>
  - [Prerequisites]()
  - [Installation]()
  - [How to check that Gradle is installed?]()
  - [When you don’t need installation?]()
</p>
</details>

3. [Gradle Overview]()
<details><summary><sub>Learn about Gradle features, core concept, and what lifecycle Gradle build has.</sub></summary>
<p>
  - [Features]()
  - [Gradle core concepts]()
  - [Build Lifecycle]()
</p>
</details>

4. [Gradle Project]
<details><summary><sub>Learn how to create basic Gradle project, and what structure it has.</sub></summary>
<p>
  - [Basic project using gradle init command]()
  - [Basic structure]()
</p>
</details>

5. [Build Script]()
<details><summary><sub>Learn how to configure Gradle build using build script, get to know basic build.gradle structure, and also some Groovy basics - Gradle DSL.</sub></summary>
<p>
  - [build.gradle(.kts)]()
    - [What can be added to the file?]()
    - [plugins]()
    - [metadata]()
    - [repositories]()
    - [dependencies]()
    - [tasks]()
  - [Groovy basics]()
</p>
</details>

6. [Gradle Wrapper]()
<details><summary><sub>Learn what is Gradle Wrapper, why it is so useful, and how to use/upgrade it.</sub></summary>
<p>
  - [Executing tasks]()
  - [Wrapper overview]()
  - [gradle vs gradlew]()
  - [Add Wrapper to the project]()
  - [Upgrade version of Gradle using Wrapper]
</p>
</details>

7. [Create Java Application]()
<details><summary><sub>Create simple Java application using different methods: init task, IDEs, or manually add Gradle to the project.</sub></summary>
<p>
  - [init task]()
  - [Manually adding Gradle]()
  - [Use IDEs]()
</p>
</details>

8. [Work with Gradle]()
<details><summary><sub>Work with Gradle using CLI or third-party tools.</sub></summary>
<p>
  - [Command-line interface]()
  - [Gradle & Third-party Tools]()
</p>
</details>

9. [Share Project]()
<details><summary><sub>Learn where Gradle stores build output, how to generate build artifacts: jar, tar or zip files, and how to publish your library.</sub></summary>
<p>
  - [Generate jar]()
  - [Distribute application]()
  - [Publish]()
</p>
</details>

10. [Multi-Project Build]()
<details><summary><sub>Learn about multi-project build structure, how to execute tasks, and how subprojects can depend on each other.</sub></summary>
<p>
  - [Declare dependencies between subprojects]()
  - [Execute tasks]()
  - [Sharing common configurations]()
</p>
</details>

11. [Troubleshooting Gradle]()
<details><summary><sub>Learn where you can ask for help in case of some Gradle issues, and what is Build Scan.</sub></summary>
<p>
  - [Places to ask]()
  - [Troubleshooting docs]()
  - [Publish and share Build Scan]()
</p>
</details>

12. [Resources]()

