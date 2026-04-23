# ☕ Maven Core Concepts — Lifecycle, POM, Dependencies

This document explains the internal working of Apache Maven, focusing on project structure, lifecycle, and dependency management.

---

## 📌 What is Maven?

Apache Maven is a build automation and dependency management tool for Java projects.

It follows **Convention over Configuration**, reducing manual setup.

---

## 📄 Project Object Model (POM)

The core of Maven is the `pom.xml` file.

It defines:
- Project metadata
- Dependencies
- Build configuration
- Plugins

---

### Example Structure

```xml
<project>
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.example</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>5.3.0</version>
    </dependency>
  </dependencies>
</project>
```

---

### 📌 Key Elements

- **groupId** → Organization/project group  
- **artifactId** → Project name  
- **version** → Project version  
- **dependencies** → External libraries required  

---

## 🔄 Maven Lifecycle (Deep Understanding)

Maven uses a predefined lifecycle to standardize builds.

### Default Lifecycle Phases

- **validate** → Checks project structure  
- **compile** → Compiles source code  
- **test** → Runs unit tests  
- **package** → Creates `.jar/.war`  
- **verify** → Runs additional checks  
- **install** → Stores artifact in local repo  
- **deploy** → Pushes artifact to remote repo  

---

### ⚙️ Important Behavior

Running:

```bash
mvn install
```

👉 Executes **all previous phases automatically**  
(validate → compile → test → package → verify → install)

---

## 📦 Dependency Management

Maven automatically downloads dependencies from remote repositories.

### Default Repository
- Maven Central

### Storage Location
```
~/.m2/repository
```

---

### 📌 How It Works

1. Reads dependencies from `pom.xml`  
2. Checks local repository (`.m2`)  
3. If not found → downloads from remote repo  
4. Caches locally for future builds  

---

## 🔌 Plugins

Maven uses plugins to perform tasks.

### Common Plugins

- **maven-compiler-plugin** → Compilation  
- **maven-surefire-plugin** → Test execution  
- **maven-jar-plugin** → Packaging  

---

### Example

```xml
<build>
  <plugins>
    <plugin>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.1</version>
    </plugin>
  </plugins>
</build>
```

---

## 📁 Standard Directory Structure

Maven follows a strict structure:

```
project/
 ├── src/
 │   ├── main/java
 │   └── test/java
 ├── pom.xml
 └── target/
```

---

## 📌 Why This Matters in DevOps

- Standard structure enables automation  
- Dependency management removes manual setup  
- Lifecycle integrates directly with CI/CD pipelines  
- Plugins allow extensibility for build workflows  

---

## 🚀 Key Takeaways

- `pom.xml` is the single source of truth  
- Maven lifecycle ensures consistent builds  
- Dependencies are automatically managed  
- Plugins extend build capabilities  
- Standardization enables scalable DevOps pipelines  
