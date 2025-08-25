**Prompt:**

**Role:** You are a QA Engineer tasked with creating a **Cucumber feature file** for one specific feature from the attached requirement document.

**Feature:** Product Page Display (or the specific feature to test)

**Constraints:**
- Include a **Background** section to set up common preconditions, e.g., user login and navigation to the product catalog.
- Each scenario must include **explicit, realistic test data** where applicable.
- **Include a data table only when a step requires multiple fields or detailed values** (e.g., product details, shipping info).
- Scenarios should be written in **Gherkin syntax** (`Given`, `When`, `Then`, `And`) and maintain **chronological order**.

**Format:** 
- Generate a **single `.feature` file** with:
  - Feature: <Feature Name>
  - Background: <Common preconditions>
  - Scenario: <Scenario Name>
    - Given / When / Then / And steps
    - Include **test data tables** only if required for the step
- Example table format for product details:
  | Field | Expected Value |
  |-------|----------------|
  | Image | High-resolution product image |
  | Description | Accurate and detailed product description |
  | Price | Correct price for the product |
  | Size Options | Available size options for the product |
  | Customer Reviews | Display of customer reviews (if applicable) |

**Additional Requirements:**
- Map test steps to the **pyramid layer** (Unit / Integration / End-to-End) as comments where applicable.
- Include at least **1 scenario** covering the core functionality of this feature.
- Ensure all test data is **realistic and consistent**.

