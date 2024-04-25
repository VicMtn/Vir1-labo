# Labo01 - Environment Setup

* [Labo description](https://cpnv-es-ngy.gitbook.io/vir1/labs/labo01-environment-setup)

## DevOps Stack to setup

Mention in this documentation the orders carried out and the results obtained.

If you have opted for a graphical installation, provide screenshots and describe the procedure up to the result obtained.

### Cloud cmd line interface - AWS Cli

```
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"\nsudo installer -pkg AWSCLIV2.pkg -target /
------
aws --version
aws-cli/2.15.39 Python/3.11.8 Darwin/23.4.0 exe/x86_64 prompt/off
```

### IDE - Intellij

```
Used the graphical installation via ToolBox : Vs:JetBrains Toolbox 2.3.0.30876, macOS 14.4.1, arm64
Intellij Vs: 2024.1
```

### Containers Engins - Docker

```
docker --version
Docker version 25.0.3, build 4debf41
```

### Versioning - Git + Git flow

```
git --version
git version 2.44.0
------
git flow version
1.12.3 (AVH Edition)
```

### IDE Plugin - Docker plugin for IntelliJ

```
Used the graphical installation for Docker plugin : 
Vs: bundled 241.14494.240
```

### Development Kit - JDK

```
java --version
openjdk 20.0.1 2023-04-18
OpenJDK Runtime Environment (build 20.0.1+9-29)
OpenJDK 64-Bit Server VM (build 20.0.1+9-29, mixed mode, sharing)
```

### Package manager - Maven

```
mvn --version
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
//TODO Schema
```

## Analysis

Answer the questions below, giving reasons for your answer (link, source).

### AWS CLI

* How does the AWS Cli interact with the cloud ?

```
//TODO answer the question
```

* What other ways do we have of dialoguing/interacting with the AWS cloud if we wanted to do without the CLI?

```
//TODO answer the question
```

* What commands do I need to run in the CLI to start an ec2 instance?

```
//TODO answer the question
```

### Docker Engine

* What type of hypervisor does Docker use?

```
//TODO answer the question
```

* What role does the Docker Desktop play in the Docker architecture?

```
//TODO answer the question
```

### Java Environment

* JDK, JRE, JVM... what's the difference?

```
//TODO answer the question
```

### Maven

* What is the command you need to use Maven to retrieve dependencies (and only that)?

```
//TODO answer the question
```


