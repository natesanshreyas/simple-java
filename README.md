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
$ path/to/java/apache-maven-3.9.6/bin/mvn -v
Apache Maven 3.9.6 (bc0240f3c744dd6b6ec2920b3cd08dcc295161ae)
Maven home: /home/antoines/java/apache-maven-3.9.6
Java version: 11.0.15, vendor: Azul Systems, Inc., runtime: /home/antoines/.cache/asbazel/output/external/remotejdk11_linux
Default locale: en, platform encoding: UTF-8
OS name: "linux", version: "5.15.133.1-microsoft-standard-wsl2", arch: "amd64", family: "unix"

```

## mvn exec

I added the maven-exec-plugin so that I could run the `pure-java-rest-api` project, and validate that everything is on the classpath.
From the `pure-java-rest-api` folder:

```shell
$ ../apache-maven-3.9.6/bin/mvn compile
[INFO] Scanning for projects...
[INFO]
[INFO] ------------< com.consulner.httpserver:pure-java-rest-api >-------------
[INFO] Building pure-java-rest-api 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ pure-java-rest-api ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /home/antoines/java/pure-java-rest-api/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ pure-java-rest-api ---
[INFO] Nothing to compile - all classes are up to date
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.519 s
[INFO] Finished at: 2024-02-20T13:40:08-05:00
[INFO] ------------------------------------------------------------------------

```

The first time you run the above it will produce tons of download output. Then run the compiled server by doing:

```shell
$ ../apache-maven-3.9.6/bin/mvn exec:java
[INFO] Scanning for projects...
[INFO]
[INFO] ------------< com.consulner.httpserver:pure-java-rest-api >-------------
[INFO] Building pure-java-rest-api 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- exec:1.4.0:java (default-cli) @ pure-java-rest-api ---
Hello World!

```

The final `Hello World!` was added by me as the first line in `Application.java` (to ensure that I am indeed compiling the right thing). You can do call the rest API it by doing a `GET` on `localhost:8000/api/hello`, passing `admin`/`admin` in a basic authentication (otherwise it returns a 401).

## Notes:

1) You cannot `mvn exec:java` if it's not already compiled. There is a way make maven automatically compile before `exec:java`, but that involves further modifying the pom.xml.
2) You can do `mvn clean` to delete the `target` folder (where compiled things go)
3) You can do `mvn clean compile` to force a complete rebuild (it's like doing `mvn clean` followed by `mvn compile`)
