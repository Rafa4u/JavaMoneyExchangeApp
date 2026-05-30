# 🧪 Java API Testing Project

A structured test suite for validating a Java application/API — covering unit, integration, and (optionally) end-to-end layers using industry-standard tools.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Running Tests](#running-tests)
- [Test Layers](#test-layers)
- [CI/CD](#cicd)
- [Contributing](#contributing)

---

## Overview

This project contains automated tests for a Java application/API. The goal is to ensure reliability, catch regressions early, and document expected behavior through tests.

> **Status:** 🚧 In progress

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Java 17+ | Language |
| Maven | Build & dependency management |
| JUnit 5 | Unit & integration testing |
| Mockito | Mocking dependencies |
| REST Assured *(optional)* | HTTP/API testing |
| GitHub Actions | CI pipeline |

> Testing frameworks will be expanded as the project evolves.

---

## Project Structure

```
├── src/
│   ├── main/java/          # Application source (if included)
│   └── test/java/
│       ├── unit/           # Unit tests
│       ├── integration/    # Integration tests
│       └── api/            # API/endpoint tests
├── pom.xml                 # Maven config & dependencies
├── .github/
│   └── workflows/
│       └── test.yml        # GitHub Actions CI
└── README.md
```

---

## Getting Started

### Prerequisites

- Java 17+ → [Download](https://adoptium.net/)
- Maven 3.8+ → [Download](https://maven.apache.org/download.cgi)

### Clone & Install

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
mvn install -DskipTests
```

---

## Running Tests

```bash
# Run all tests
mvn test

# Run a specific test class
mvn test -Dtest=YourTestClassName

# Run a specific method
mvn test -Dtest=YourTestClassName#methodName

# Run only unit tests (if tagged)
mvn test -Dgroups="unit"

# Generate test report
mvn surefire-report:report
```

Reports are generated at `target/surefire-reports/`.

---

## Test Layers

### Unit Tests
Isolated tests for individual classes and methods. Dependencies are mocked with **Mockito**.

```java
@Test
void shouldReturnUserById() {
    when(userRepository.findById(1L)).thenReturn(Optional.of(mockUser));
    User result = userService.getById(1L);
    assertEquals("Rafa", result.getName());
}
```

### Integration Tests
Tests that verify how components interact (e.g., service + repository layers).

### API Tests *(planned)*
End-to-end HTTP tests against the running application using **REST Assured** or similar.

---

## CI/CD

Tests run automatically on every push and pull request via **GitHub Actions**.

`.github/workflows/test.yml`:

```yaml
name: Java Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      - name: Run tests
        run: mvn test
```

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feat/your-test`
3. Commit your changes: `git commit -m "test: add tests for X"`
4. Push and open a Pull Request

---

## License

MIT — feel free to use and adapt.# JavaMoneyExchangeApp
simple project test in java
