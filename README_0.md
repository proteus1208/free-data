# pentaho-platform

## Overview

This project consists of modules that form the core platform and business analytics server, providing essential services for enterprise reporting, content management, scheduling, and administration.

## Core Modules

### API
Provides common interfaces used throughout the platform, including APIs for the plugin system, repository, security, and other platform services.

### Core
Contains core implementations of platform subsystems and utility classes.

### Repository
Provides the JCR Jackrabbit repository implementation for the Pentaho platform.

### Scheduler
Contains the Quartz-based scheduler implementation for managing scheduled platform tasks.

### Extensions
Provides additional capabilities and extensions used across different areas of the platform.

### User Console
Provides a GWT-based frontend that allows users to navigate the repository, execute and schedule content, and administer the platform.

### Assemblies
Builds the Pentaho Server distribution package and includes the samples and additional resources required by the server.

## How to Build

The Pentaho platform uses Maven as its build framework.

### Prerequisites

- Maven 3 or later
- Java JDK 11
- Maven configuration file (`settings.xml`) placed in the `.m2` directory under your user home directory.

### Build the Project

Run the following command from the project root:

```bash
mvn clean install
```

To skip tests during the build:

```bash
mvn clean install -DskipTests
```

The resulting Pentaho Server package is generated in:

```text
assemblies/pentaho-server/
```

### Running Tests

**Unit Tests**

Run all unit tests across the project and its submodules:

```bash
mvn test
```

To debug a specific unit test using the default remote debugging port (5005):

```bash
cd core
mvn test -Dtest=YourTest -Dmaven.surefire.debug
```

**Integration Tests**

Run integration tests across platform modules:

```bash
mvn verify -DrunITs
```

Run a specific integration test:

```bash
mvn verify -DrunITs -Dit.test=YourIT
```

Run a specific integration test in remote debugging mode:

```bash
mvn verify -DrunITs -Dit.test=YourIT -Dmaven.failsafe.debug
```

### Build Without Running Tests

```bash
mvn clean install -DskipTests
```

### Save Build Output to a Log File

```bash
mvn clean install test > log.txt
```

## IntelliJ IDEA Configuration

Avoid using IntelliJ IDEA's bundled Maven installation. Configure the IDE to use the same Maven version as your command-line environment.

Navigate to:

**Project Settings → Build, Execution, Deployment → Build Tools → Maven → Maven Home Directory**

