**Prompt:**

**Role:** You are a QA Engineer tasked with creating **Cypress step definitions** for a given Cucumber feature file.

**Feature File:** Product Page Display (as provided)

**Requirements:**
- Generate **step definitions** in **JavaScript** using **Cypress** and **Cucumber preprocessor** syntax (`Given`, `When`, `Then`).
- Each step in the feature file must have a corresponding Cypress step definition.
- Use **realistic test data** from the feature file.
- Include **comments** indicating what the step does.
- Handle **UI interactions**, including:
  - Navigating to pages
  - Clicking buttons or links
  - Entering text in input fields
  - Verifying page content or elements
  - Handling data tables for multi-field verification
- Organize the step definitions clearly, grouping them by **Background**, **Scenarios**, and **Data Table handling**.
- Use **Cypress best practices** such as `cy.get()`, `cy.contains()`, and `cy.should()`.

**Additional Requirements:**
- Include **selectors or placeholders** for elements, so they can be easily replaced with real CSS/XPath selectors.
- Ensure step definitions are **reusable** across scenarios.
- Include **error handling** for assertions where appropriate.

