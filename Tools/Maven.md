# Maven

### Java Compliation

- Source Code ==== Complie(javac) ====> .class File ==== Run(java)

### Java Packaging

- **.jar** – A packaged Java archive (zip) containing compiled class files.
  ```
    jar cf demoJar.jar HelloWorld.class
    // java -classpath demoJar.jar HelloWorld
  ```
- **.war** – A web application archive with classes, JARs, and web resources.
- **.ear**– An enterprise archive that bundles multiple WAR files.
- **Fat JAR (Uber JAR)** – A single executable JAR that includes all dependencies (commonly used in Spring Boot).
- **Docker Container** – A lightweight package with the JVM, Java app, and runtime environment.

### Maven Repository

- A Maven repository is a location where Maven stores all the project artifacts (like JARs, dependencies, plugins, metadata, etc.) that it needs for building and running projects.
- Types
  - Local
    - Located on your machine (by default: ~/.m2/repository).
    - Stores all the dependencies you’ve downloaded once, so you don’t need to fetch them again.
  - Central
    - A public repository maintained by the Apache Maven community.
  - Remote
    - Custom repositories hosted by organizations, teams, or third-party providers.
- Repository Search Order => Local --> Remote --> Central

### Maven Commands

- mvn clean → Cleans the environment by deleting the target/ folder where compiled classes and packaged artifacts are stored.

- mvn compile → Compiles the source code of the project and places .class files into the target/classes directory.

- mvn test → Runs unit tests using the testing framework (e.g., JUnit, TestNG). Test reports are generated under target/surefire-reports.

- mvn package → Compiles the code, runs tests, and packages the project into a distributable format (.jar, .war, etc.) inside target/.

- mvn install → Installs the packaged project into the local Maven repository (~/.m2/repository) so other projects can use it as a dependency.

- mvn deploy → Copies the final package to a remote repository for sharing with other developers/teams.

- mvn validate → Validates the project setup and ensures that all information is correct before proceeding with the build.

- mvn verify → Runs checks and integration tests to verify that the package is valid.

### Maven Plugins

- Maven Clean Plugin
  - Purpose: Its main function is to remove files that were generated during the build process.
  - Default Action: By default, it achieves this by deleting the /target directory from the project's root folder.
- Maven Compiler Plugin
  - Goals: It has two goals, which are compiler:compile and compiler:testCompile.
  - Java Version: The default source and target language levels are set to Java 1.6, though the Apache team recommends setting these values explicitly.
- Maven Resources Plugin
  - Purpose: It is designed to copy a project's resources into an output directory, which is typically the target directory.
  - Goals: It has three goals: resources:resources, resources:testResources, and resources:copy-resources.
- Maven Surefire Plugin
  - Purpose: The Surefire plugin is used to execute the unit tests for a project.
  - Supported Frameworks: It supports JUnit 3, JUnit 4, JUnit 5, and TestNG by default.
- Maven JAR Plugin

  - Purpose: Its function is to build JAR files from the project's compiled artifacts and resources.
  - Goals: It has two primary goals: jar:jar and jar:test-jar.

- Maven Deploy Plugin
  - Purpose: This plugin is used to deploy the project's artifacts to remote Maven repositories.
  - Usage: Deployment is frequently performed in a Continuous Integration (CI) environment, and its configuration is usually part of the Maven POM file.
- Maven Site Plugin
  - Lifecycle: It operates within the SITE build lifecycle, which is distinct from the CLEAN and DEFAULT lifecycles used by the other plugins.
  - Goals: It is a feature-rich plugin with seven goals, including site:site to generate the project's website and site:deploy to deploy it.
  ````
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.11.0</version>
          <configuration>
            <source>17</source>
            <target>17</target>
          </configuration>
        </plugin>
        ```
  ````

### POM

```
  <project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo-project</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <name>Demo Project</name>
    <description>A sample Maven project</description>

    <properties>
        <java.version>17</java.version> <!-- You can set this to 8, 11, 17, etc. -->
        <maven.compiler.source>${java.version}</maven.compiler.source>
        <maven.compiler.target>${java.version}</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Example dependency: JUnit for testing -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>

```

- mvn dependency:tree → Displays the project’s dependency hierarchy (useful for resolving version conflicts).

- mvn dependency:list → Lists all dependencies used in the project.

- mvn dependency:analyze → Analyzes which dependencies are declared but not used, or used but not declared.

- mvn spring-boot:run → (Spring Boot projects only) Runs the application directly without needing to package it first.

- mvn archetype:generate → Creates a new Maven project from a template (archetype).
