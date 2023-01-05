# 2. How to Install?

## Prerequisites

Java JDK version 8 or higher. 
Check version using command `java -version`.

## Installation

Follow instruction provided here: https://gradle.org/install/

*If you have Mac, the easiest way will be to install using Homebrew [^1].*

`brew install gradle`

## How to check that Gradle is installed?

Using command `gradle -v`. Result should be as follows:
```
------------------------------------------------------------
Gradle 5.6.4
------------------------------------------------------------
```
<sub>Your version of Gradle may differ.</sub>

## When you don’t need installation?
- If you receive **ready** Gradle project, you can execute Gradle build with Gradle Wrapper using commands `gradlew` and/or `gradlew.bat` (more about these scripts in [Wrapper](https://github.com/yanamlnk/gradle-notes/tree/main/contents/6-gradle-wrapper) section)
- Wrapper invokes a declared version of Gradle, and download it beforehand if necessary. 
- To run the project using `gradlew`, it needs to have generated Wrapper files.

[^1]: [The Missing Package Manager](https://brew.sh) for macOS (or Linux)

#   
|:arrow_left: [BACK](https://github.com/yanamlnk/gradle-notes/blob/main/contents/1-what-is-build-tool/README.md)|[TABLE OF CONTENTS](https://github.com/yanamlnk/gradle-notes#table-of-contents)|[NEXT](https://github.com/yanamlnk/gradle-notes/blob/main/contents/3-gradle-overview/README.md) :arrow_right:|
| --- | --- | --- |
