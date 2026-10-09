# APS SDK Project Archetype

[![Maven Central](https://img.shields.io/maven-central/v/io.github.alfresco-aps-sdk/aps-project-archetype.svg)](https://central.sonatype.com/artifact/io.github.alfresco-aps-sdk/aps-project-archetype)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Documentation](https://img.shields.io/badge/docs-portal-brightgreen.svg)](https://alfresco-aps-sdk.github.io/)
[![Organization](https://img.shields.io/badge/GitHub-alfresco--aps--sdk-0969da.svg)](https://github.com/alfresco-aps-sdk)
[![Commercial Support](https://img.shields.io/badge/Support-TAI%20Solutions-orange.svg)](https://www.taisolutions.com/)

Maven Archetype to bootstrap complete, production-ready **Alfresco Process Services (APS) SDK 3.x** projects with a single command. Publicly available on **Maven Central**.

---

## Quickstart: Generating a New Project

To generate a new APS project, run:

```bash
mvn archetype:generate \
  -DarchetypeGroupId=io.github.alfresco-aps-sdk \
  -DarchetypeArtifactId=aps-project-archetype \
  -DarchetypeVersion=3.1.3 \
  -DgroupId=com.example \
  -DartifactId=my-aps-project \
  -Dversion=1.0.0-SNAPSHOT \
  -Dpackage=com.example.aps \
  -DinteractiveMode=false
```

Once generated, enter your new project directory:

```bash
cd my-aps-project
```

---

## Generated Project Structure

The archetype creates a modular Maven reactor project containing:

```text
my-aps-project/
├── pom.xml                                 # Root reactor POM with profiles for APS 24.x, 25.x, 26.x
├── aps-extensions-jar/                     # Custom Java logic, delegates, event listeners, REST APIs
├── activiti-app-overlay-war/               # Custom webapp overlay combining extensions with APS WAR
├── activiti-app-overlay-docker/            # Docker Compose orchestration and Dockerfiles
├── activiti-app-integration-tests/         # End-to-end integration tests using REST client
├── license/
│   └── README.md                           # Instructions for APS and Aspose license files
├── run.sh                                  # Automation script (build, docker start/stop/purge)
└── run.bat                                 # Windows automation script
```

> [!NOTE]
> **License Files**: As per Alfresco software distribution policies, **`activiti.lic`** and **`transform.lic`** are **not** bundled with this archetype. Before running your APS Docker environment or full test suite, place your valid enterprise licenses in the `license/` folder.

---

## Building and Running the Generated Project

### 1. Compile and Unit Test
```bash
mvn clean test
```

### 2. Run with Docker Compose
```bash
./run.sh start
```
Or with Windows:
```cmd
run.bat start
```

This launches:
- PostgreSQL database
- Elasticsearch instance
- APS Tomcat engine with your custom extensions overlayed at `http://localhost:8080/activiti-app`
- APS Admin application at `http://localhost:8081/activiti-admin`

To stop:
```bash
./run.sh stop
```

---

## Building This Archetype Locally

If you are developing or customizing the archetype itself:

```bash
git clone https://github.com/alfresco-aps-sdk/aps-project-archetype.git
cd aps-project-archetype
mvn clean install
```

This registers the archetype into your local Maven cache (`~/.m2/repository`), allowing you to immediately run `mvn archetype:generate`.

---

## Enterprise Support & Consulting

Commercial support, enterprise consulting, and custom training for Alfresco Process Services and APS SDK are provided by **[TAI Solutions](https://www.taisolutions.com/)**.

---

## License

This project is licensed under the [Apache License, Version 2.0](LICENSE.txt).
