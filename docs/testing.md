---
sidebar_position: 5
---

# Testing & Quality

[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ashtonav_opentimezone&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=ashtonav_opentimezone)
[![.NET](https://github.com/ashtonav/opentimezone/actions/workflows/dotnet.yml/badge.svg)](https://github.com/ashtonav/opentimezone/actions/workflows/dotnet.yml)

OpenTimezone uses two main types of tests to ensure code quality:

1. [**Unit Tests**](#1-unit-tests)
2. [**Functional Tests**](#2-functional-tests)

---

## 1. Unit Tests

- **Framework**: [NUnit](https://nunit.org/)
- **Location**: Housed in a project named `Timezone.UnitTests`.
- **Purpose**:
    - Verify the logic of individual methods or classes in isolation.
    - Ensure that changes in the code do not break existing functionality.

### How to Run Unit Tests

You can run the unit tests in one of the following ways:

- **Visual Studio**:
    1. Open the solution in Visual Studio.
    2. Go to **Test > Test Explorer**.
    3. **Run tests** within the **Timezone.UnitTests** project.

---

## 2. Functional Tests

- **Framework**: [Reqnroll](https://reqnroll.net/) using Gherkin syntax.
- **Location**: Housed in a project named `Timezone.FunctionalTests`.
- **Purpose**:
    - Validate the **end-to-end behavior** of the API by simulating real usage scenarios.
    - Ensure that the API meets expected outcomes when various inputs are given.

### How to Run Functional Tests

1. **Visual Studio**:
    1. Open the solution in Visual Studio.
    2. Go to **Test > Test Explorer**.
    3. **Run tests** within the **Timezone.FunctionalTests** project.

---
