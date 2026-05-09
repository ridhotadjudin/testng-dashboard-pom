![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium_4.0.0-43B02A?style=flat-square&logo=selenium&logoColor=white)
![TestNG](https://img.shields.io/badge/TestNG_7.6.0-FF7300?style=flat-square&logo=testng&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apachemaven&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)

# 🧪 TestNG + Selenium POM — Cicool Dashboard

Automated test suite for the **Cicool Dashboard** application using Java, Selenium 4, and TestNG with the **Page Object Model** design pattern. Features data-driven testing powered by an Excel data provider and organized test execution via TestNG XML suites.

---

## 📑 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Getting Started](#-getting-started)
- [Test Scenarios](#-test-scenarios)
- [Design Patterns](#-design-patterns)
- [Reports](#-reports)
- [Author](#-author)

---

## ✨ Features

- **Page Object Model** — Clean separation between test logic and page interactions
- **Data-Driven Testing** — Excel-powered parameterization using `testng-ext-dataprovider`
- **TestNG XML Suites** — Structured test execution with `CicoolPOMSuite.xml`
- **Screenshot Capture** — Automatic screenshots saved to `hasilScreenshot/` on test events
- **Multi-Page Coverage** — Tests spanning sign-in, dashboard, CRUD builder, and password recovery
- **Maven Build** — Dependency management and lifecycle execution via Maven

---

## 🛠 Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| Java | 11+ | Programming language |
| Selenium WebDriver | 4.0.0 | Browser automation |
| TestNG | 7.6.0 | Test framework and execution |
| Maven | 3.x | Build and dependency management |
| testng-ext-dataprovider | 14.2.0 | Excel-based data provider for TestNG |
| Apache POI | — | Excel file reading (transitive dependency) |

---

## 📁 Project Structure

```
testng-dashboard-pom/
├── src/
│   ├── main/java/
│   │   └── pages/
│   │       ├── SignInPage.java             # Sign-in page object
│   │       ├── HomePage.java               # Home page object
│   │       ├── Dashboard.java              # Dashboard page object
│   │       ├── CrudBuilderPage.java        # CRUD builder page object
│   │       └── ForgotPasswordPage.java     # Forgot password page object
│   └── test/java/
│       └── tests/
│           ├── LoginFunctionality.java     # Login functional tests
│           └── TestLoginUser.java          # Data-driven login tests
├── testdata/
│   └── LoginTestCase - Ridho.xlsx          # Excel test data
├── hasilScreenshot/                        # Captured screenshots
├── CicoolPOMSuite.xml                      # TestNG suite configuration
├── pom.xml                                 # Maven project configuration
└── README.md
```

---

## 📋 Prerequisites

- **Java JDK** 11 or higher
- **Apache Maven** 3.6+
- **Google Chrome** browser
- **ChromeDriver** matching your Chrome version

---

## 🚀 Getting Started

### Installation

```bash
# Clone the repository
git clone https://github.com/ridhotadjudin/testng-dashboard-pom.git
cd testng-dashboard-pom

# Install dependencies
mvn clean install -DskipTests
```

### Running Tests

```bash
# Run the full TestNG suite
mvn test -DsuiteXmlFile=CicoolPOMSuite.xml

# Run a specific test class
mvn test -Dtest=LoginFunctionality

# Run data-driven login tests
mvn test -Dtest=TestLoginUser
```

---

## 🧪 Test Scenarios

| Scenario Name | Type | Description |
|---|---|---|
| Valid Sign-In | Functional | Verifies successful login with correct credentials and dashboard redirection |
| Invalid Sign-In | Negative | Validates error messages for incorrect username/password combinations |
| Dashboard Access | Functional | Confirms authenticated users can access all dashboard sections and widgets |
| CRUD Operations | Functional | Tests create, read, update, and delete actions on the CRUD builder page |
| Forgot Password | Functional | Validates the password recovery flow including email input and confirmation |
| Data-Driven Login | Data-Driven | Executes login tests against multiple credential sets from `LoginTestCase - Ridho.xlsx` |
| Screenshot on Failure | Utility | Verifies that screenshots are automatically captured and saved on test failures |

---

## 🏗 Design Patterns

### Page Object Model (POM)

Each application page is represented by a dedicated Java class that encapsulates all element locators and interaction methods. Test classes interact with pages through clean, descriptive method calls rather than raw Selenium commands:

```
SignInPage → enterUsername(), enterPassword(), clickLogin()
Dashboard  → navigateToSection(), verifyWidgetVisible()
```

This provides a single point of maintenance when the UI changes and makes tests highly readable.

### Data Provider Pattern

The `testng-ext-dataprovider` library reads test data directly from Excel spreadsheets and injects it into TestNG test methods via the `@DataProvider` annotation. Each row in `LoginTestCase - Ridho.xlsx` becomes a separate test iteration, enabling comprehensive input coverage without code changes.

### Suite Configuration Pattern

`CicoolPOMSuite.xml` defines test grouping, execution order, and parallel configuration. This XML-driven approach allows flexible test orchestration — running smoke tests, regression suites, or individual features by simply specifying a different suite file.

---

## 📊 Reports

| Report | Location | Description |
|---|---|---|
| TestNG HTML Report | `test-output/index.html` | Detailed test results with pass/fail breakdown per suite and test method |
| Screenshots | `hasilScreenshot/` | Visual evidence captured during test execution for debugging and documentation |
| Surefire Report | `target/surefire-reports/` | Maven-generated execution report compatible with CI/CD dashboards |

View the TestNG report after a test run:

```bash
start test-output\index.html
```

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Ridho Tadjudin**

[![Website](https://img.shields.io/badge/Website-ridhotadjudin.id-blue?style=flat-square&logo=google-chrome&logoColor=white)](https://ridhotadjudin.id)
[![GitHub](https://img.shields.io/badge/GitHub-ridhotadjudin-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/ridhotadjudin)
