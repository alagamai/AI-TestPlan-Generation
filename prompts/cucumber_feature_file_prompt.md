**Prompt:**

**Role:** You are a QA Engineer tasked with creating a **Cucumber feature file** for the attached requirement document.

**Functionality:** Registration, Login, Cart, Checkout, Seller Dashboard

**Constraints:**
- Include a **Background** section to set up preconditions common to multiple scenarios (e.g., navigating to the homepage, logging in as a user).
- Each scenario should include **realistic, explicit test data** for every step requiring input. Examples:
  - Names, emails, and passwords for user accounts
  - Product IDs, names, and prices for catalog actions
  - Shipping addresses and payment card numbers for checkout
- Scenarios should be written in **Gherkin syntax** (`Given`, `When`, `Then`, `And`) and be easy to read and maintain.
- Include at least **10 meaningful scenarios**, covering critical, normal, and optional flows.

**Format:** 
- Generate a **single `.feature` file**.
- Structure:
  - Feature: <Feature Name>
  - Background: <Common preconditions>
  - Scenario: <Scenario Name>
    - Given / When / Then / And steps
    - Include **explicit test data** in every step requiring input
- Add **comments** to indicate the **pyramid layer** (Unit, Integration, End-to-End) where applicable.

**Additional Requirements:**
- Scenarios must be **chronological** to reflect the full user journey.
- Provide **combined end-to-end flows** that go from registration to checkout.
- Make all test data **realistic and consistent** across scenarios (e.g., the same email for login after registration).

