**Prompt:**

**Role:** You are a QA Engineer tasked with creating **Playwright step definitions** for a given Cucumber feature file.

**Feature File:** Product Page Display (as provided)

**Requirements:**
- Generate **step definitions** in **JavaScript or TypeScript** using **Playwright Test Runner** and **Cucumber preprocessor** syntax (`Given`, `When`, `Then`).
- Each step in the feature file must have a corresponding Playwright step definition.
- Use **realistic test data** from the feature file.
- Include **comments** describing what each step does.
- Handle **UI interactions**, including:
  - Navigating to pages (`page.goto`)
  - Clicking buttons or links (`page.click`)
  - Entering text in input fields (`page.fill`)
  - Verifying page content or elements (`page.locator().shouldHaveText()` / `expect`)
  - Handling data tables for multi-field verification
- Organize the step definitions clearly, grouping them by **Background**, **Scenarios**, and **Data Table handling**.
- Use **Playwright best practices** such as `await page.locator().click()`, `await expect(locator).toHaveText()`, and proper async/await handling.

**Additional Requirements:**
- Include **selectors or placeholders** for elements, so they can be easily replaced with real CSS/XPath selectors.
- Ensure step definitions are **reusable** across scenarios.
- Include **error handling** for assertions where appropriate.
- Include **data tables** only when required, for steps with multiple fields like product details.

