Here’s a **very basic SonarQube project** you can set up quickly for practice 🚀

---

# 🔹 Basic SonarQube Project

## 📌 Overview

SonarQube is a tool for **static code analysis** that helps detect bugs, vulnerabilities, and code smells.
We’ll set up SonarQube using **Docker Compose** and connect it with a **simple application**.

---

## 🛠️ Prerequisites

* Docker & Docker Compose installed
* Minimum VM/Server: **2 CPU, 4 GB RAM**
* Open Ports: **9000** (SonarQube UI), **22** (SSH)

---

## 📂 Project Structure

```
sonarqube-basic-project/
├── docker-compose.yml
├── app/
│   └── Hello.java
└── sonar-project.properties
```

---

## 📜 `docker-compose.yml`

```yaml
version: "3"

services:
  sonarqube:
    image: sonarqube:community
    container_name: sonarqube
    ports:
      - "9000:9000"
    environment:
      - SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions

  db:
    image: postgres:13
    environment:
      - POSTGRES_USER=sonar
      - POSTGRES_PASSWORD=sonar
      - POSTGRES_DB=sonar
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  sonarqube_data:
  sonarqube_extensions:
  postgres_data:
```

---

## 📜 Example Java File (`app/Hello.java`)

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, SonarQube!");
    }
}
```

---

## 📜 SonarQube Config (`sonar-project.properties`)

```properties
sonar.projectKey=hello-project
sonar.projectName=Hello Project
sonar.projectVersion=1.0
sonar.sources=./app
sonar.language=java
sonar.sourceEncoding=UTF-8
```

---

## ▶️ Steps to Run

1. **Start SonarQube**

   ```bash
   docker-compose up -d
   ```

2. **Access Dashboard**
   Go to 👉 `http://localhost:9000`
   Default login: `admin / admin`

3. **Install Scanner**

   ```bash
   sudo apt-get install unzip
   wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-5.0.1.3006-linux.zip
   unzip sonar-scanner-*.zip
   export PATH=$PATH:$(pwd)/sonar-scanner-*/bin
   ```

4. **Run Analysis**

   ```bash
   sonar-scanner
   ```

5. **Check Results**
   In SonarQube UI → Projects → `Hello Project`

---

✅ This is the **minimal setup** for a SonarQube project.
You can later expand with **Maven/Gradle builds**, CI/CD (GitHub Actions, Jenkins), and multiple languages.

---

Do you want me to make this repo **GitHub-ready** (with README.md, `.gitignore`, and setup steps) so you can directly push and demo it?
