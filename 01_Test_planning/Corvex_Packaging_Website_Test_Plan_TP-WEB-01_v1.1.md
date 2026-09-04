# User Acceptance Test Plan: Corvex Packaging E-commerce Website

Identifier: TP-WEB-01  
Test Level: User Acceptance Testing (UAT)  
Current Status: Completed  
Version: v1.1  
Date: 2026-08-03  
Author: Annalie Prinsloo  

---

## 1. Document Control
### 1.1 Revision History
| Version | Date | Author | Description of Changes |
| :--- | :--- | :--- | :--- |
| 1.1 | 2026-08-03 | Annalie Prinsloo | Baseline UAT Test Plan for Corvex Packaging |

### 1.2 References
* Corvex Packaging Live Website (<https://corvex-packaging.example>)
* ISTQB Foundation Level Syllabus (CTFL v4.0)
* Selenium WebDriver Documentation
* PyTest and pytest-bdd Automation Framework Documentation
* Gherkin Documentation

---

## 2. Test Objectives
The primary objective of this User Acceptance Testing (UAT) phase is to evaluate the usability, functionality, and cross-platform responsiveness of the Corvex Packaging website. Testing ensures that key core system flows—specifically catalog navigation, keyword and SKU search capabilities, product filtering, and the customer quote list interaction—behave reliably across designated desktop and mobile (for responsive layout validation only) environments. This phase will validate that the live system meets business standards and provides an acceptable user experience.

---

## 3. Context & Scope
### 3.1 Context of Testing (System Under Test)
The System Under Test (SUT) is the **Corvex Packaging Website (Live Environment)** accessed via Windows 11 desktop and Android 16 platforms. This phase validates end-user journeys including content readability, interactive layouts, automated regressions, and functional components.

### 3.2 Features to be Tested (In-Scope)
* **`REQ-KS-01` (Automated Gherkin Scenarios Keyword Search):** Keyword queries matching single, multiple, partial and plural parameters (e.g., "wrap", "bubble wrap", "bub" and "wraps").
* **`REQ-SKU-02` (Automated Gherkin Scenarios SKU Search):** Validation of accurate direct product retrieval using precise SKU codes (e.g., "AIR010", "BRO0104", "CAT030", "PAL41" and "FOO226").
* **`REQ-IS-03` (Automated Gherkin Scenarios Invalid Search):** Error handling validation for blank submissions and random non-alphanumeric string injections (e.g. "" and "123@456").
* **`REQ-CF-04` (Automated Gherkin Category Filtering):** Verifying user navigation workflows selecting structural master categories, drilling down to specific sub-filters, and matching store inventory layouts.
* **`REQ-LN-05` (Manual Scenarios Link Navigation):** Validation of page routing loops across primary Header Nav Bars, comprehensive multi-column footers, and floating social sidebar indices.
* **`REQ-MQF-06` (Manual Quote List Functionality):** Adding single/multiple iterations of inventory entries, checking active counter badge increments, managing item line removals, and validating UI view appearances.
* **`REQ-NS-07` (Manual Newsletter Signup):** Validating contextual rules for the "Stay in the loop" modal popup using valid, empty, and malformed email syntax inputs.
* **`REQ-RL-08` (Manual Responsive Layout Validation):** UI breakpoints verification checking visibility and click-interaction properties of search boxes and navigation menus across Desktop, Mobile Portrait, and Mobile Landscape orientations.

### 3.3 Features Not Tested (Out-of-Scope)
* **Contact Page Validation:** Functional processing inputs and field validations located directly inside the dedicated "Contact Us" page forms.
* **Submitting Quote Process:** The final end-to-end checkout processing chain, back-end quote submission storage, and outbound notification emails.

### 3.4 Assumptions, Constraints and Dependencies
* **Assumptions:**
    * The production environment of the Corvex Packaging website remains stable with zero unexpected server-side downtime during active execution.
* **Constraints:**
    * Tests are strictly restricted to the specified browser matrix editions available on the active test nodes.
    * Automation testing depends entirely on element selector stability within the current live page DOM tree.
* **Dependencies:**
    * Network availability to reach external servers.
    * Valid product inventory must continuously exist in the live database to satisfy target test parameters (e.g., SKU "AIR010").

---

## 4. Physical Device & Environment Matrix
| Device Model | Operating system | Browser / UI Version | Environment type |
| :--- | :--- | :--- | :--- |
| Lenovo Ideapad 3 Laptop | Windows 11 | Chrome, Firefox, Headless Chrome | Local Physical Desktop |
| Samsung Galaxy S25 FE | Android 16 | Mobile Chrome / Samsung One UI 8.5 | Local Physical Mobile phone | 

---

## 5. Test Strategy & Approach
### 5.1 Test Levels and Test Types
* **Test Level:** User Acceptance Testing (UAT)
* **Test Types:**
    * **Functional Testing:** Verifying that system workflows operate strictly according to search, navigation, and cart criteria.
    * **Non-Functional Testing:**
        * **Usability/Accessibility Testing:** Manual visual checking of element styling, overlap errors, and ease of interaction for end consumers.
        * **Portability Testing:** Testing behavior across disparate browser viewports and shifting mobile screen coordinates.
    
### 5.2 Testing Methodologies & Techniques
* **Black-box Techniques:** Testing system outputs entirely via surface UI presentation elements without reading underlying source code.
    * **Specification-based Techniques:** Equivalence Partitioning and Boundary Value Analysis applied explicitly to search strings and email syntax input structures.
* **Scenario Specification Approach: Behavior-Driven Development (BDD):** Using Gherkin syntax (Given-When-Then) to define human-readable test scenarios that map directly to automated scripts.

### 5.3 Test Automation Approach
* The automation suite will be developed using **PyTest** as the core test runner, combined with **pytest-bdd** to parse Gherkin feature files. 
* **Selenium WebDriver** (Python bindings) will drive the browser interactions. 
* **Gherkin** `.feature` files will store the high-level business behaviors, while Python step-definitions will implement the underlying Selenium automation code. 
* Tests will execute concurrently across the target browser matrix (Chrome, Headless Chrome and Firefox).

---

## 6. Entry, Exit & Suspension Criteria
### 6.1 Entry Criteria
* Target production website (<https://corvex-packaging.example>) is fully accessible with active product listings.
* Selenium automated execution framework is verified, compiled, and ready to target the local desktop infrastructure.
* Manual test devices are charged, operational, and connected to test networks.
* Gherkin feature files for in-scope requirements are finalized, peer-reviewed, and committed to the repository.

### 6.2 Exit Criteria (Acceptance Criteria)
* 100% of defined automated search and filtering routines execute successfully across Chrome, Firefox, and Headless Chrome.
* Critical manual functional components (Navigation routines, Quote management and Newsletter validation) do not reveal blocking functional failures.
* Layout elements adjust dynamically across all designated responsive breakpoints without blocking user actions.

### 6.3 Suspension & Resumption Criteria
* **Suspension Criteria:** System issues unexpected 5xx server exceptions or production platform undergoes unplanned maintenance downtime.
* **Resumption Criteria:** Platform administrators declare structural site services restored and verified operational.

### 6.4 Test Monitoring & Control
#### 6.4.1 Metrics Collected
* Test case execution progress: % of planned test cases (manual and automated) executed to date.
* Pass/fail rate: % of executed test cases passing, tracked against the Exit Criteria thresholds in Section 6.2.
* Defect metrics: open defect count by severity, logged against BUG-WEB-01 onward.
* Requirements coverage: % of in-scope requirements (REQ-KS-01 to REQ-RL-08) with at least one passing test case or automated scenario, tracked via the RTM (RTM-WEB-01).
* Automation stability: automated scenario pass rate across the target browser matrix (Chrome, Firefox, Headless Chrome).

#### 6.4.2 Reporting Cadence
* Progress is reviewed against each milestone defined in Section 7.4, with a status summary recorded at the completion of each milestone.
* Execution Logs (EL-WEB-01) are updated on each test session, providing a continuous record between milestones.

#### 6.4.3 Control Actions
* If defect density or severity trends indicate a blocking risk to Exit Criteria (Section 6.2), remaining execution is re-prioritized toward the highest-risk requirements (see Section 8.2 Product Risks) before continuing lower-priority coverage.
* If a Suspension Criterion (Section 6.3) is triggered, testing halts and is resumed only once the corresponding Resumption Criterion is met.
* Any deviation from the schedule in Section 7.4 is documented in the Test Report (TSR-WEB-01) along with the root cause.

---

## 7. Logistics, Resources & Schedule
### 7.1 Test Environment & Tools Requirements
* Python environment configured with PyTest, pytest-bdd, and Selenium WebDriver bindings.
* Unrestricted HTTP/HTTPS communication channels targeting the production system endpoints.

### 7.2 Roles, Responsibilities & Staffing
* **UAT Project Lead & Execution Specialist**: Annalie Prinsloo
    * *Responsibilities:* Owns framework setup, automated script development, manual user session checking, defect entry logs, and delivery summaries.

### 7.3 Work Breakdown & Estimates
| Task Item | Target Resource | Estimated Effort |
| :--- | :--- | :--- |
| Writing test documentation | Annalie Prinsloo | 40 Hours |
| Drafting and reviewing Gherkin Feature Files (`REQ-KS-01` to `REQ-CF-04`) | Annalie Prinsloo | 4 Hours |
| Implementing PyTest step definitions and Selenium WebDriver code bindings | Annalie Prinsloo | 16 Hours |
| Manual Execution Sessions (`REQ-LN-05` to `REQ-RL-08`) | Annalie Prinsloo | 4 Hours |
| Defect Analysis, Retesting, and Final Reporting | Annalie Prinsloo | 8 Hours |

### 7.4 Milestones & Schedule
* **Milestone 1:** Automation scripts finalized and verified locally — 2026-08-12
* **Milestone 2:** Manual execution passes on mobile targets completed — 2026-08-19
* **Milestone 3:** Final sign-off and summary closure distribution completed — 2026-08-28

---

## 8. Communication & Risk Management
### 8.1 Communication Protocols & Status Reporting
* Test status documentation and execution logs will be updated immediately upon the completion of both automated runs and manual cycles.

### 8.2 Product Risks (Quality Risks)
| Risk ID | Risk Description | Impact level | Mitigation Action |
| :--- | :--- | :--- | :--- |
| **QR-01** | Heavy rendering lags or page asset slowdowns break element selection hooks during automated Selenium runs. | Medium | Incorporate programmatic explicit waits checking for visual element presence before executing interactive calls. |
| **QR-02** | Broken link endpoints within footer categories generate 404 page routing paths for consumers. | High | Automated crawler loops run at the beginning of the cycle to pinpoint and flag dead hyperlinks early. |

### 8.3 Project Risks (Management Risks)
| Risk ID | Risk Description | Impact level | Mitigation Action |
| :--- | :--- | :--- | :--- |
| **MR-01** | Sudden changes to live layout elements break specific DOM selector bindings during active automation schedules. | Medium | Utilize robust CSS class identifiers and resilient fallback XPath patterns to minimize structural layout sensitivity. |

---

## 9. Deliverables
* **Test Plan:** This document (TP-WEB-01 v1.1)
* **Gherkin Feature Files & PyTest-Selenium Automation Repository:** `https://github.com/AnnaliePrinsloo1/Corvex_Ecommerce_Website_UAT_Testware.git`
* **Requirements Traceability Matrix (RTM)**: RTM-WEB-01
* **Test Conditions**: TCOND-WEB-01
* **Test Cases Suite**: TC-WEB-01
* **Test Charters**: TCHAR-WEB-01
* **Test Procedures**: TPROC-WEB-01
* **Manual Execution Log**: EL-WEB-01
* **Defect Reports**: BUG-WEB-01 to BUG-WEB-04
* **Test Report**: TSR-WEB-01

Check if this test plan does satisfy the requirements for test monitoring and control. Suggested: A monitoring/control section (metrics, reporting cadence, exit criteria).