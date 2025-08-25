**Prompt:**

**Role:** You are a QA Engineer tasked with creating a **Playwright step definition skeleton** for a given Cucumber feature file.

**Feature File:** Product Page Display (as provided)

**Requirements:**
- Generate **step definitions in TypeScript** using **Playwright Test Runner** and **Cucumber preprocessor** syntax (`Given`, `When`, `Then`).
- Include **browser and page setup/teardown** using `Before` and `After` hooks.
  - Launch browser (headless or non-headless)
  - Create a new page
  - Close browser after tests
- Implement **all steps from the feature file** as skeletons with **placeholders** for:
  - URLs
  - Selectors
  - Test data
- Include **async/await** properly for Playwright actions.
- Include **data table handling** for steps that verify multiple fields (like product details).
- Add **comments** indicating where the real selectors or values should be filled.
- Ensure **reusable steps** for multiple scenarios.

**Additional Requirements:**
- Use **best practices** for Playwright (`page.goto`, `page.click`, `page.fill`, `page.locator`, `expect`).
- Do not include real selectors or URLs; use placeholders like `YOUR_..._SELECTOR` and `YOUR_URL_HERE`.
- Keep the code **readable and well-structured**, grouped by **Background**, **Scenarios**, and **Data Table handling**.
- Return the **output in Markdown code block format** with TypeScript syntax highlighting.

