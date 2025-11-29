# ⭐ 1. **How did you optimize your Maven or Gradle build?**

### **Maven optimization**

✔ Enable parallel builds

```
mvn -T 1C clean install
```

✔ Use dependency management
✔ Avoid snapshot dependencies in production
✔ Use incremental build (`mvn -o`)
✔ Reduce plugin executions
✔ Use `.mvn/jvm.config` to allocate better memory
✔ Exclude unused transitive dependencies
✔ Use `maven-dependency-plugin` to analyze tree:

```
mvn dependency:tree
```

### **Gradle optimization**

✔ Enable **Gradle daemon** (enabled by default)
✔ Enable **parallel execution**:

```
org.gradle.parallel=true
```

✔ Enable **build cache**:

```
org.gradle.caching=true
```

✔ Use **incremental tasks**
✔ Use **Kotlin DSL** for stricter compile-time checks
✔ Avoid overuse of annotation processors (Lombok, MapStruct)
✔ Avoid `compileOnly` dependencies incorrectly

**Result:** Build time dropped 40–70% in real projects.

---

# ⭐ 2. **How do you handle dependency conflicts in a real project?**

### Step 1 — Check dependency tree

**Maven**:

```
mvn dependency:tree -Dverbose -Dincludes=log4j
```

**Gradle**:

```
./gradlew dependencies --configuration compileClasspath
```

### Step 2 — Resolve by:

✔ Forcing a version

```xml
<dependencyManagement>
   <dependency>
     <groupId>com.fasterxml.jackson.core</groupId>
     <artifactId>jackson-databind</artifactId>
     <version>2.15.3</version>
   </dependency>
</dependencyManagement>
```

✔ Excluding transitive dependencies

```xml
<dependency>
  <groupId>spring-boot-starter-web</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
  <exclusions>
    <exclusion>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
    </exclusion>
  </exclusions>
</dependency>
```

✔ In Gradle:

```groovy
implementation('org.example:abc:1.0') {
    exclude group: 'commons-logging'
}
```

✔ Using **BOM (Bill of Materials)** for consistent versions
✔ Testing locally via integration tests

---

# ⭐ 3. **How do you enforce logging standards in your team?**

✔ Create **logging guidelines**:

* INFO only for business steps
* DEBUG for troubleshooting
* ERROR only when business failures
* Mask PII data (passwords, tokens)
* No System.out.println()

✔ Use a custom `LoggerUtil` wrapper:

```java
public class LogUtil {
    public static void infoWithUser(Logger logger, String userId, String message) {
        logger.info("[user:{}] {}", userId, message);
    }
}
```

✔ Use **MDC** for request correlation
✔ Add linting rules (Checkstyle / SonarQube) to enforce logging patterns
✔ Review logging in PRs
✔ Enable **Spring Boot logging rotation** for production

---

# ⭐ 4. **What issues you faced with Lombok in real projects?**

✔ Missing IDE plugin → getters/setters not visible
✔ Conflicts with MapStruct annotation processor
✔ Inheritance issues with @Builder
✔ @Data generating incorrect equals()/hashCode()
✔ Harder to debug (generated code not visible)
✔ Version conflicts with Java 17+
✔ Serialization issues with @Builder classes
✔ Reflection-based libraries failing due to missing constructor

**Fix:** Use `delombok`, avoid @Data in entities, prefer @Value for immutability.

---

# ⭐ 5. **How do you troubleshoot a production logging issue?**

### Typical scenario:

➡ Logs not appearing
➡ Log rotation failing
➡ Incorrect log level
➡ Too many logs → disk full
➡ MDC missing values

### Steps:

1. Check **effective configuration**

   * Logback prints debug logs:

     ```
     -Dlogback.debug=true
     ```
2. Check file permissions
3. Check disk full
4. Restart application if logback.xml not hot-reloadable
5. Validate appenders are correct
6. Reproduce with lower log level
7. Check if async logging queue is full (Log4j2 async mode)
8. Check Spring Boot default logback override
9. Validate MDC usage for multi-thread logs

**Final fix example:** Fixed missing UUID in MDC by adding MDC.clear() in finally block.

---

# ⭐ 6. **Convert a Maven project to Gradle**

### Step 1 — Delete pom.xml

### Step 2 — Create build.gradle

```groovy
plugins {
    id 'java'
}

group = 'com.example'
version = '1.0'

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.3'
}

test {
    useJUnitPlatform()
}
```

### Step 3 — Generate wrapper

```
gradle wrapper
```

### Step 4 — Run build

```
./gradlew build
```

---

# ⭐ 7. **Write a Lombok-based POJO using @Builder**

```java
import lombok.Builder;
import lombok.Data;

@Data
@Builder
public class Employee {
    private String name;
    private int salary;
    private String department;
}
```

Usage:

```java
Employee emp = Employee.builder()
                        .name("John")
                        .salary(50000)
                        .department("IT")
                        .build();
```

---

# ⭐ 8. **Configure Logback with rolling logs**

`src/main/resources/logback-spring.xml`

```xml
<configuration>

    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>logs/app.log</file>

        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>logs/app-%d{yyyy-MM-dd}.log</fileNamePattern>
            <maxHistory>7</maxHistory>
        </rollingPolicy>

        <encoder>
            <pattern>%d %-5level [%thread] %logger - %msg%n</pattern>
        </encoder>
    </appender>

    <root level="INFO">
        <appender-ref ref="FILE"/>
    </root>

</configuration>
```

✔ Daily rotation
✔ Keeps last 7 files
✔ Writes to /logs folder

---

# ⭐ 9. **Write your own custom Maven plugin (explanation)**

### Step 1 — Add plugin project structure

Create a Maven project containing:

`MyCustomPlugin.java`

```java
@Mojo(name = "hello")
public class MyCustomPlugin extends AbstractMojo {

    @Parameter(property = "name", defaultValue = "World")
    private String name;

    public void execute() throws MojoExecutionException {
        getLog().info("Hello " + name + " from Maven Plugin!");
    }
}
```

### Step 2 — Build plugin

```
mvn install
```

### Step 3 — Use plugin in another project

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.example</groupId>
            <artifactId>custom-plugin</artifactId>
            <version>1.0</version>
        </plugin>
    </plugins>
</build>
```

Run:

```
mvn custom-plugin:hello -Dname=Mathu
```

---

# ⭐ 10. **Demonstrate Multi-module Maven project**

Folder structure:

```
parent/
  pom.xml
  module-a/
      pom.xml
  module-b/
      pom.xml
```

### parent pom.xml

```xml
<project>
  <modules>
    <module>module-a</module>
    <module>module-b</module>
  </modules>
</project>
```

### module-a pom.xml

```xml
<project>
  <parent>
    <groupId>com.demo</groupId>
    <artifactId>parent</artifactId>
    <version>1.0</version>
  </parent>

  <artifactId>module-a</artifactId>
</project>
```

### module-b pom.xml

```xml
<project>
  <parent>
    <groupId>com.demo</groupId>
    <artifactId>parent</artifactId>
    <version>1.0</version>
  </parent>

  <artifactId>module-b</artifactId>

  <dependencies>
     <dependency>
        <groupId>com.demo</groupId>
        <artifactId>module-a</artifactId>
        <version>1.0</version>
     </dependency>
  </dependencies>
</project>
```

Run:

```
mvn clean install
```

✔ Common dependencies managed by parent
✔ Modules built in correct order
✔ Excellent for microservices + shared libraries

---

# ⭐ Final Interview Summary

| Topic                     | Key Takeaway                           |
| ------------------------- | -------------------------------------- |
| Build optimization        | Parallel builds, cache, incremental    |
| Dependency conflicts      | BOM, excludes, version constraints     |
| Logging standards         | MDC, masking, correct levels           |
| Lombok issues             | Debugging, equals, builder inheritance |
| Prod logging debugging    | Enable logback debug, check appenders  |
| Maven → Gradle conversion | Simple build.gradle migration          |
| Lombok builder            | Cleaner POJO design                    |
| Logback rolling logs      | TimeBasedRollingPolicy                 |
| Custom Maven plugin       | Mojo + annotation                      |
| Multi-module Maven        | Parent POM + module structure          |

---

g.xml** optimized for production
✔ A **complete multi-module Gradle project** template
