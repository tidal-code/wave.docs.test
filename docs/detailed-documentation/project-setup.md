---
layout: default
title: Project Setup
parent: Detailed Docs
nav_order: 17
---

# Project Setup - Tools and Settings

Tidal Wave UI automation library is built with Java and Selenium. To set up an automation project using Tidal, you need to configure a few software yourself.


### Java

If you haven't already configured Java in your system please navigate to [Microsoft Open JDK.](https://learn.microsoft.com/en-us/java/openjdk/download#openjdk-11){:target='_blank'}

1. Download the Windows/Mac version as per your system and install it in your system following the prompts from the installer.

2. Setup JAVA_HOME variable to your system

    Under the "System Variables" section, click "New" to add a new variable.
    Set the variable name as "JAVA_HOME" and the variable value as the path to your JDK installation directory (e.g., C:\Program Files\Java\jdk-11.x.x).
    Edit the "Path" variable and append "%JAVA_HOME%\bin" at the end.
    Click "OK" to save the changes.

3. Test the setup by running the command `java -version`


### Maven

1. Visit the Apache [Maven website](https://maven.apache.org/download.cgi){:target='_blank'}

2. Download the latest binary zip archive.

3. Extract the contents of the downloaded zip file to a directory of your choice (e.g., C:\maven).

4. Set up the MAVEN_HOME environment variable:

    Under the "System Variables" section, click "New" to add a new variable.
    Set the variable name as "MAVEN_HOME" and the variable value as the path to your Maven installation directory (e.g., C:\maven\apache-maven-x.x.x).
    Edit the "Path" variable and append "%MAVEN_HOME%\bin" at the end.
    Click "OK" to save the changes.

5. Test the installation by running the command `mvn -version`  


### IntelliJ Idea

1. Visit the JetBrains [IntelliJ IDEA website](https://www.jetbrains.com/idea/download/){:target='_blank'}

2. Download the community edition or ultimate edition of IntelliJ IDEA.

3. Run the installer and follow the installation wizard's instructions.

4. Launch IntelliJ IDEA after installation.

5. Install the plugins 'Cucumber' and 'Gherkin' if you are working with BDD

6. Configure your project settings to use 'Java 11' version if you are using a higher JDK version.