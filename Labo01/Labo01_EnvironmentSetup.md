# Labo01 - Environment Setup

* [Labo description](https://cpnv-es-ngy.gitbook.io/vir1/labs/labo01-environment-setup)

## DevOps Stack to setup

Mention in this documentation the orders carried out and the results obtained.

If you have opted for a graphical installation, provide screenshots and describe the procedure up to the result obtained.

### Cloud cmd line interface - AWS Cli

```
> curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"\nsudo installer -pkg AWSCLIV2.pkg -target /
------
> aws --version
aws-cli/2.15.39 Python/3.11.8 Darwin/23.4.0 exe/x86_64 prompt/off
```

### IDE - Intellij

```
Used the graphical installation via ToolBox : Vs:JetBrains Toolbox 2.3.0.30876, macOS 14.4.1, arm64
Intellij Vs: 2024.1
```

### Containers Engine - Docker

```
> docker --version
Docker version 25.0.3, build 4debf41
```

### Versioning - Git + Git flow

```
> git --version
git version 2.44.0
------
> git flow version
1.12.3 (AVH Edition)
```

### IDE Plugin - Docker plugin for IntelliJ

```
Used the graphical installation for Docker plugin : 
Vs: bundled 241.14494.240
```

### Development Kit - JDK

```
> java --version
openjdk 20.0.1 2023-04-18
OpenJDK Runtime Environment (build 20.0.1+9-29)
OpenJDK 64-Bit Server VM (build 20.0.1+9-29, mixed mode, sharing)
```
So add to redo the installation of the right version of Java

```
Check the JMV installed : 
> ls /Users/your_user/Library/Java/JavaVirtualMachines/
 jbr-17.0.7 jdk-20.0.1
```
Then needed to export the JAVA_HOME
```
Check the version installed : actually 20.0.1
> Export the JAVA_HOME : export JAVA_HOME=/Users/your_user/Library/Java/JavaVirtualMachines/jbr-17.0.7/Contents/Home
```
Then check the version
```
> java --version 
java 17.0.11 2024-04-16 LTS
Java(TM) SE Runtime Environment (build 17.0.11+7-LTS-207)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.11+7-LTS-207, mixed mode, sharing)
```

### Package manager - Maven

```
> mvn --version
Apache Maven 3.9.6 (bc0240f3c744dd6b6ec2920b3cd08dcc295161ae)
Maven home: /opt/homebrew/Cellar/maven/3.9.6/libexec
Java version: 21.0.2, vendor: Homebrew, runtime: /opt/homebrew/Cellar/openjdk/21.0.2/libexec/openjdk.jdk/Contents/Home
Default locale: fr_CH, platform encoding: UTF-8
OS name: "mac os x", version: "14.4.1", arch: "aarch64", family: "mac"
```

## Schema

Show your development environment, mentioning all the components in the stack.

Identify the links between components.

```
find th file in the folder 
```

## Analysis

Answer the questions below, giving reasons for your answer (link, source).

### AWS CLI

* How does the AWS Cli interact with the cloud ?

```
The AWS CLI interact with the cloud by making various requests to AWS services. When the command is executed the requests is send to the dedicated AWS services.
```

* What other ways do we have of dialoguing/interacting with the AWS cloud if we wanted to do without the CLI?

```
Using the Home Console of AWS
```

* What commands do I need to run in the CLI to start an ec2 instance?

```
aws ec2 run-instances --option (your image, your instances type or key-name)
```

### Docker Engine

* What type of hypervisor does Docker use?

```
Docker doesn't use a hypervisor but use the Containerization system
```

* What role does the Docker Desktop play in the Docker architecture?

```
Docker desktop is directly connected to the Docker Daemon and send requests or command to it. Wich allow the user to manage the containers more easily and help to focus on code instead of heavy settings
```

### Java Environment

* JDK, JRE, JVM... what's the difference?

```
JDK : Is like the tools box containing all the needed
JRE : Is the environnement where the Java code is executed
JVM : Is the machine that virtualize Java and where the software run
```

### Maven

* What is the command you need to use Maven to retrieve dependencies (and only that)?

```
mvn dependency:resolve
```


