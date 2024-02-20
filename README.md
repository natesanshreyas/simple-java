# README.md

This is a directory containing a few java projects. The goal is to figure out how to use the platform to improve java UX.

## Which projects?

- [pure-java-rest-api](https://github.com/piczmar/pure-java-rest-api)
  - not a spring or spring boot proejct
  - uses java 11

- [FizzBuzzEnterpriseEdition](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition)
  - uses the spring framework (not spring boot)
  - uses java 7
  - uses maven 2.3

- [spring-boot-examples](https://github.com/in28minutes/spring-boot-examples)
  - 20+ spring-boot examples
  - use a parent POM [spring-boot-starter-parent](https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-parent)
  - use java 17
  - use maven 3.1

## Which java?

```shell
$ which java
/path/to/THR/third_party/bin/java

$ java --version
openjdk 11.0.15 2022-04-19 LTS
OpenJDK Runtime Environment Zulu11.56+19-CA (build 11.0.15+10-LTS)
OpenJDK 64-Bit Server VM Zulu11.56+19-CA (build 11.0.15+10-LTS, mixed mode)

```

## Which mvn?

- Downloaded file [apache-maven-3.9.6-bin.tar.gz](https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz)
- Installed using: `tar xzvf apache-maven-3.9.6-bin.tar.gz` ([Installation instructions](https://maven.apache.org/install.html))
- `mvn.sh` to avoid polluting my PATH

```shell
$ ./mvn.sh -v
Apache Maven 3.9.6 (bc0240f3c744dd6b6ec2920b3cd08dcc295161ae)
Maven home: /home/antoines/java/apache-maven-3.9.6
Java version: 11.0.15, vendor: Azul Systems, Inc., runtime: /home/antoines/.cache/asbazel/output/external/remotejdk11_linux
Default locale: en, platform encoding: UTF-8
OS name: "linux", version: "5.15.133.1-microsoft-standard-wsl2", arch: "amd64", family: "unix"

```
