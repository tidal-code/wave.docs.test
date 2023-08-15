---
layout: default
parent: 
nav_order: 1
permalink: hidden/maven
---

<!-- ## Future Releases -->



# Maven Project Creation

## How to create a maven project in Sonatype

Here’s the list of requirements your project needs to meet,

- Supply correct and complete Javadoc
- Supply sources
- Sign each file using GPG/PGP
- Provide correct coordinates for the project (groupID, artifactID, version)
- Project name, description, and URL
- License information (MIT license could be used)
- Developer information
- SCM information (Github in this case)

For JavaDoc and source code, recommend using the already existing Maven plugins called `maven-javadoc-plugin`
 and `maven-source-plugin`
, respectively. Add each plugin into your pom.xml file.

```xml
<build>
    <plugins>
    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-source-plugin</artifactId>
        <version>2.2.1</version>
        <executions>
            <execution>
                <id>attach-sources</id>
                <goals>
                    <goal>jar-no-fork</goal>
                </goals>
            </execution>
        </executions>
    </plugin>
    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-javadoc-plugin</artifactId>
        <version>2.9.1</version>
        <executions>
        <execution>
            <id>attach-javadocs</id>
            <goals>
                <goal>jar</goal>
            </goals>
        </execution>
    </executions>
    </plugin>
    </plugins>
</build>
```

All files deployed need to be signed with GPG/PGP. A .ASC file containing the signature must be included for each file.

The files you should deploy are,

- example-1.0.0.pom
- example-1.0.0.jar
- example-1.0.0-sources.jar
- example-1.0.0-javadoc.jar

The previous files will be automatically generated with the source and javadoc plugins we just installed.

The signed files you need to include are,

- example-1.0.0.pom.asc
- example-1.0.0.jar.asc
- example-1.0.0-sources.jar.asc
- Example-1.0.0-javadoc.jar.asc

To sign our files we need to download GPG from [http://www.gnupg.org/download/](https://web.archive.org/web/20220120022316/https://www.gnupg.org/download/). Depending on your system, use the GPG or GPG2 `--version` command to verify it has been properly installed. (I will stick with GPG2 commands from now on)

Now we proceed to create a key using this command,

`gpg2 --gen-key`

In response, you will be asked for,

- Size, select 2048bit.
- Encryption, RSA.
- Time validity, select two years (*i.e.*, that’s the convention).
- Then, enter your name, description, and email.
- Finally, choose a secure passphrase for your key.

To list your keys, use,

`gpg2 --list-keys`

```cmd
[Antonio-2:~ antoniohernandez$ gpg2 --list-keys
/Users/antoniohernandez/.gnupg/pubring.kbx
pub
uid sub
rsa2048 2017-06-14 [SC] [expires: 2019-06-14]
C3F26754EA46DE8767E5770B6624CAB739783EED
[ultimate] Antonio Hernandez <ghernandez@nearsoft.com>
rsa2048 2017-06-14 [E] [expires: 2019-06-14]

```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/03d2992d-917d-4e66-b8fa-06580728f201/Untitled.png)

The one piece of info that matters to us is the keyID. This is the long character chain starting with C3F2675.

Maven Central needs to verify our signed files with our public key. To publish your key, use the following commands,

`gpg2 --keyserver hkp://pool.sks-keyservers.net --send-keys C3F26754EA46DE8767E5770B6624CAB739783EED`

If you are not on the US, you will probably have trouble with this. Let me help you save hours of frustration,

`gpg2 --keyserver hkp://ipv4.pool.sks-keyservers.net --send-keys C3F26754EA46DE8767E5770B6624CAB739783EED`

Adding `ipv4` to the domain should do the trick.

## **Sign Your Files**

We are ready to sign our files. Let’s do this with a plugin called `maven-gpg-plugin`.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4c65815-23bc-459e-8f55-0041cb066012/Untitled.png)

But for this plugin to work we need to modify the `settings.xml` file found on either of these two locations,

- The Maven install: ${Maven.home}/conf/settings.xml
- A user’s install: ${user.home}/.m2/settings.xml

Find it and add the following,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/12262bbb-9565-403f-9c73-42f8e4783b10/Untitled.png)

This is needed to tell Maven where to find all the required info to sign our files.

Since your project must be unique in Maven Central, you need to make sure to specify correct coordinates (groupID, artifactID, version). Also, developers will need to know how to find your project that is why project name, description, and URL need to be specified.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9e1a5b84-b848-4aa8-8380-4236abea4efd/Untitled.png)

You also need to be specify the license info on the pom file. Since we are all about Open Source here, we can use the MIT license,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa7777b8-7f41-4012-8fef-63d880a58f37/Untitled.png)

You also need to include a developers section,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c9fdadf-999f-4a5c-9ae9-a457c4c397e6/Untitled.png)

Finally, you need to add to your Source Control System to your pom file.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/da0a1add-0212-4a3a-ae56-defec35a201a/Untitled.png)

## **Are We There, Yet?**

Now we meet all the requirements Maven asks for. But we are missing something important.

Since we are looking to publish our Open Source project to the Maven Central repository, we will use the [Open Source Software Repository Hosting](https://web.archive.org/web/20220120022316/http://central.sonatype.org/pages/ossrh-guide.html). This is an approved repository provided by Sonatype. We will deploy to the OSSRH and our artifact will be available in the Central Repository.

For this we need to create a ticket with Sonatype,

- Create your [JIRA account](https://web.archive.org/web/20220120022316/https://issues.sonatype.org/secure/Signup!default.jspa)
- Create a [New Project ticket](https://web.archive.org/web/20220120022316/https://issues.sonatype.org/secure/CreateIssue.jspa?issuetype=21&pid=10134)

Then adding some more configuration to our pom,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a583dc3-67e4-46c1-9724-27127fa979de/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/19aeb354-172e-42c3-a63b-79aa469d2752/Untitled.png)

And some more configuration to authenticate using your recently created JIRA account to our settings.xml file.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2723e3de-cf70-4082-bea2-5e4ba914fb0d/Untitled.png)

At the end your pom file should look like this.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>example-lib</artifactId>
    <version>1.0.0</version>

    <name>ExampleLib</name>
    <description>Example Library</description>
    <url>https://github.com/Example/example-lib</url>

    <licenses>
        <license>
            <name>MIT License</name>
            <url>http://www.opensource.org/licenses/mit-license.php</url>
            <distribution>repo</distribution>
        </license>
    </licenses>

    <developers>
        <developer>
            <name>John Doe</name>
            <email>jdoe@example.com</email>
            <organization>Example Co.</organization>
            <organizationUrl>http://www.example.com</organizationUrl>
        </developer>
    </developers>

    <scm>
        <url>https://github.com/Example/example-lib/tree/master</url>
    </scm>

    <dependencies>         

        <!-- Your dependencies here -->

    </dependencies>

    <distributionManagement>
        <snapshotRepository>
            <id>ossrh</id>
            <url>https://oss.sonatype.org/content/repositories/snapshots</url>
        </snapshotRepository>
        <repository>
            <id>ossrh</id>
            <url>https://oss.sonatype.org/service/local/staging/deploy/maven2/</url>
        </repository>
    </distributionManagement>

    <build>
        <plugins>
            <!-- Your plugins here -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-javadoc-plugin</artifactId>
                <executions>
                    <execution>
                        <id>attach-javadocs</id>
                        <goals>
                            <goal>jar</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-source-plugin</artifactId>
                <executions>
                    <execution>
                        <id>attach-sources</id>
                        <goals>
                            <goal>jar-no-fork</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-gpg-plugin</artifactId>
                <version>1.5</version>
                <executions>
                    <execution>
                        <id>sign-artifacts</id>
                        <phase>verify</phase>
                        <goals>
                            <goal>sign</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>

            <plugin>
                <groupId>org.sonatype.plugins</groupId>
                <artifactId>nexus-staging-maven-plugin</artifactId>
                <version>1.6.7</version>
                <extensions>true</extensions>
                <configuration>
                    <serverId>ossrh</serverId>
                    <nexusUrl>https://oss.sonatype.org/</nexusUrl>
                    <autoReleaseAfterClose>true</autoReleaseAfterClose>
                </configuration>
            </plugin>

        </plugins>
    </build>
</project>
```

Note: The usage of <repositories> and <pluginRepositories> is strongly discouraged by Maven.

We have finished all configuration and we are ready to deploy to the staging repository after receiving an email notice indicating that your New Project ticket is Resolved.

If this is a release version (does not end in `-SNAPSHOT` and with the property `autoReleaseAfterClose` set to true), you can run a deployment to OSSRH and an automated release to the Central Repository with the usual,

`mvn clean deploy`

With the property `autoReleaseAfterClose` set to false you can manually inspect the staging repository in the Nexus Repository Manager and trigger a release of the staging repository later with,

`mvn nexus-staging:release`







