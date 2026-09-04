<div align="center">

### Tech Stack
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Selenium](https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white)
[![BDD - Gherkin](https://shields.io/badge/BDD-Gherkin-71BF44?style=for-the-badge&logo)](https://cucumber.io)
![Pytest](https://img.shields.io/badge/pytest-%23ffffff.svg?style=for-the-badge&logo=pytest&logoColor=2f9fe3)
![Markdown](https://img.shields.io/badge/markdown-%23000000.svg?style=for-the-badge&logo=markdown&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)

### Testing Scope
![UAT](https://img.shields.io/badge/UAT-000080?style=for-the-badge&logo)
![Functional](https://img.shields.io/badge/Functional-000080?style=for-the-badge&logo)

### Test Environment
![Google Chrome](https://img.shields.io/badge/Google%20Chrome-4285F4?style=for-the-badge&logo=GoogleChrome&logoColor=white)
![Firefox](https://img.shields.io/badge/Firefox-FF7139?style=for-the-badge&logo=Firefox-Browser&logoColor=white)
![Windows](https://custom-icon-badges.demolab.com/badge/Windows-0078D6?style=for-the-badge&logo=windows11&logoColor=white)
![Samsung](https://img.shields.io/badge/Samsung-%231428A0.svg?style=for-the-badge&logo=samsung&logoColor=white&logoSize=auto)

### Documentation reviewed with
![Claude](https://img.shields.io/badge/claude-%23D97757.svg?style=for-the-badge&logo=claude&logoColor=white)

</div>

# Corvex Packaging E-Commerce Website - End-to-End User Acceptance Test (UAT) & Automation Showcase

*Note on confidentiality: The company name, branding, and domain used in this repository have been fictionalized. Manual testing engagements are confidential by nature and cannot be publicly disclosed; this repository demonstrates the same process, documentation standards, and automation approach applied on real client work, using a fictional project so it can be shared openly as a portfolio piece.*

An end-to-end user acceptance testing (UAT) testware repository showcasing a combined manual exploratory approach and a Python-based BDD automation framework (`PyTest` + `pytest-bdd` + `Selenium WebDriver`), structured to reflect the ISTQB Foundation Level (CTFL v4.0) fundamental test process.

This repository hosts the complete testware suite, execution records, and automation code for the UAT validation of a fictional e-commerce platform, **Corvex Packaging** (<https://corvex-packaging.example>). 

The primary objective of this project was to validate core transactional e-commerce paths across desktop and physical mobile devices. This showcase combines manual exploratory testing (for visual responsive layouts, global navigation paths, and multi-item quote features) with behavior-driven automation (for keyword/SKU queries and catalog filtering) to demonstrate complete requirements traceability coverage.

## Contents
- [Physical Device & Environment Matrix](#physical-device--environment-matrix)
- [Test Process Documentation Structure](#test-process-documentation-structure)
- [Validation Methodologies & Test Quality Metrics](#validation-methodologies--test-quality-metrics)
- [Technical Installation & Local Automation Setup](#technical-installation--local-automation-setup)
- [Active Test Cycle Insights](#active-test-cycle-insights)
- [About the QA Professional](#about-the-qa-professional)


---

## Physical Device & Environment Matrix
Testing was distributed across targeted physical infrastructures to catch both browser layout anomalies and real-world mobile processing quirks that cannot be simulated:

* **Desktop Environment (Automation & Manual Layout Nodes):** Lenovo Ideapad 3 Laptop | Windows 11 | Google Chrome, Mozilla Firefox, Headless Chrome (automated runs).
* **Mobile Environment (Manual Charter Execution Target):** Samsung Galaxy S25 FE | Android 16 | Mobile Chrome | Samsung One UI 8.5.

---

## Test Process Documentation Structure
The repository is organized into sequential testing phases to maintain a clear, auditable execution record:


```text
├── README.md                         
├── 01_Test_planning/
│   └── Corvex_Packaging_Website_Test_Plan_TP-WEB-01_v1.1.md
├── 02_Test_analysis/
│   ├── Corvex_Packaging_Website_RTM-WEB-01_v1.1.md
│   └── Corvex_Packaging_Website_Test_Conditions_TCOND-WEB-01_v1.1.md
├── 03_Test_design/
│   ├── Corvex_Packaging_Website_Test_Charters_TCHAR-WEB-01_v1.1.md
│   └── Corvex_Packaging_Website_Manual_Test_Cases_TC-WEB-01_v1.1.md
├── 04_Test_implementation/
│   └── Corvex_Packaging_Website_Test_Procedures_TPROC-WEB-01_v1.1.md
├── Test_Automation/
│   ├── features/ 
│   │   ├── navigation.feature
│   │   └── search.feature    
│   ├── pages/
│   │   ├── __init__.py
│   │   ├── navigation.py 
│   │   ├── result.py
│   │   └── search.py     
│   ├── tests/
│   │   ├── conftest.py
│   │   ├── test_navigation_steps.py       
│   │   └── test_search_steps.py 
│   ├── config.json
│   ├── Pipfile
│   ├── Pipfile.lock
│   └── pytest.ini 
├── 05_Test_execution/
│   ├── Execution_Logs/
│   │   └── Corvex_Packaging_Website_Execution_Log_EL-WEB-01_v1.1.md
│   ├── Defect_Reports/
│   │   ├── Corvex_Packaging_Website_Defect_Report_BUG-WEB-01.md
│   │   ├── Corvex_Packaging_Website_Defect_Report_BUG-WEB-02.md
│   │   ├── Corvex_Packaging_Website_Defect_Report_BUG-WEB-03.md
│   │   ├── Corvex_Packaging_Website_Defect_Report_BUG-WEB-04.md
│   │   ├── Screenshot_BUG-WEB-03.png
│   │   └── Screenshot_BUG-WEB-04.png
└── 06_Test_completion/
    └── Corvex_Packaging_Test_Report_TSR-WEB-01_v1.1.md
     

```

**Note:** Automation code is kept in a single folder outside the phase structure so it can be cloned independently. Conceptually, the artifacts still map to the ISTQB test process as follows:

| **Automation artifact** | **Conceptually maps to** |
| :--- | :--- |
| `features/*.feature` | Test Design (test cases, expressed as Gherkin scenarios) |
| `pages/`, `tests/` (step defs, page objects) | Test Implementation (automated test scripts) |
| `pytest.ini`, `config.json`, `Pipfile` | Test Implementation (test environment/config) |
| Execution results / CI run logs | Test Execution |

---

## Validation Methodologies & Test Quality Metrics
* **Behavior-Driven Automation Architecture:** Used Gherkin feature files (`Given-When-Then`) to translate stakeholder requirements into executable test scenarios, implemented with PyTest and Selenium WebDriver.
* **Parameterized Test Design:** Refactored repetitive manual test cases into parameterized Gherkin `Scenario Outlines` with `Examples:` tables, reducing duplication across similar test inputs.
* **Exploratory Testing:** Used time-boxed test charters to evaluate visual UI responsiveness, orientation changes (portrait vs. landscape), and touch target behavior under real-world usage conditions.
* **Specification-Based Test Design:** Applied Boundary Value Analysis (BVA) and Equivalence Partitioning (EP) to form field inputs (newsletter string boundaries) and search query patterns (partial and plural terms).
* **Traceability:** Maintained requirement-to-test linkage (`REQ-KS-01` to `REQ-RL-08`) across Gherkin feature files, manual test cases, execution logs, and defect reports.

---

## Technical Installation & Local Automation Setup

Follow these steps to clone this project repository, install the automated browser testing suite via Pipenv, and run the test scripts.

### Prerequisites
* **Python 3.10+** installed on your machine.
* **Pipenv** installed globally (`pip install pipenv` if you don't have it yet).
* A terminal or **Command Prompt (CMD)** interface.
* Google Chrome installed (Selenium Manager will automatically fetch and manage the matching WebDriver binary behind the scenes).

### 1. Clone the Project Repository
Open your terminal, navigate to your desired directory workspace, and run:
```bash
git clone https://github.com/AnnaliePrinsloo1/Corvex_Ecommerce_Website_UAT_Testware.git
cd Corvex_Ecommerce_Website_UAT_Testware/Test_Automation
```

### 2. Install Framework Dependencies
Pipenv creates an isolated virtual environment and installs the exact dependency versions pinned in `Pipfile.lock` (PyTest, pytest-bdd, and Selenium WebDriver) in one step:
```bash
pipenv install
```

### 3. Activate the Virtual Environment
```bash
pipenv shell
```
*(Confirmation: your prompt will show the environment name in parentheses, e.g. `(test_automation)`.)*

To verify all packages installed correctly, you can run:
```bash
pipenv run pip list
```

### 4. Running the Automation Scripts Suite
Thanks to the configuration in the project-level `pytest.ini`, you can launch custom testing scopes using tags. Run these either inside an active `pipenv shell` session, or prefix each command with `pipenv run` if you skipped Step 3.

* **Execute the complete automation test runner package:**
```bash
  pytest
```
* **Run only the Core Smoke Verification flows (`REQ-KS-01` — Keyword Searches):**
```bash
  pytest -m smoke
```
* **Run only the Target SKU Redirect scripts (`REQ-SKU-02`):**
```bash
  pytest -m sku
```
* **Exclude negative boundary test configurations from execution runs:**
```bash
  pytest -m "automated and not negative"
```

---

## Active Test Cycle Insights
* **Total Automated Scenarios Executed:** 13 (including parameterized Scenario Outline iterations)
* **Total Manual Scenarios Executed:** 31 distinct verification steps
* **Deployment Release Status:** Pending hotfixes for open responsive components.

### Open Defects Summary
| Defect ID | Description | Severity | Priority |
| :--- | :--- | :--- | :--- |
| `BUG-WEB-01` | Single/multiple keyword search returns irrelevant results alongside relevant ones | Major | High |
| `BUG-WEB-02` | Plural search terms return zero results | Major | High |
| `BUG-WEB-03` | Quote list quantity silently resets after navigating away and back | Critical | High |
| `BUG-WEB-04` | Promotional text elements render cut off in mobile landscape orientation | Minor | Low |

*Severity reflects technical/functional impact; Priority reflects business urgency to fix — per the [ISTQB Glossary](https://istqb-glossary.page/), these are assessed independently rather than interchangeably.*

---

## About the QA Professional
I am an **ISTQB® Certified Freelance Software Tester** specializing in end-to-end **User Acceptance Testing (UAT)** and digital quality assurance. I partner with businesses to validate and optimize high-impact digital products before market launch, ensuring seamless user experiences and functional reliability across multiple platforms.

### Core Areas of Expertise:
* **Web Application QA:** Cross-browser compatibility validation, responsive web design (RWD) testing, BDD automation framework assembly, and functional regression testing.
* **E-Commerce Platforms:** End-to-end checkout flow validation, shopping cart state persistence, search engine routing parameters, and localized user journey verification.
* **Mobile Application Testing:** Native Android app validation, physical device matrix testing, hardware-software interaction testing, and interruption handling.
