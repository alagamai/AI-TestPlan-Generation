```javascript
import { Given, When, Then, Before, After } from "cypress-cucumber-preprocessor/steps";

// ---------------------
// Hooks for setup and teardown (optional in Cypress)
// ---------------------
Before(() => {
  // Cypress automatically handles browser launch
  // You can put global setup here if needed
  cy.log("Starting test scenario...");
});

After(() => {
  cy.log("Test scenario finished.");
});

// ---------------------
// Background Steps
// ---------------------
Given('the user has valid login credentials', () => {
  cy.wrap({ email: 'YOUR_EMAIL_HERE', password: 'YOUR_PASSWORD_HERE' }).as('userCredentials');
});

Given('the user is on the login page', () => {
  cy.visit('YOUR_LOGIN_PAGE_URL'); // TODO: Replace with actual login page URL
});

When('the user enters email {string} and password {string}', (email, password) => {
  cy.get('YOUR_EMAIL_SELECTOR').type(email); // TODO: Replace selector
  cy.get('YOUR_PASSWORD_SELECTOR').type(password); // TODO: Replace selector
});

When('clicks the Login button', () => {
  cy.get('YOUR_LOGIN_BUTTON_SELECTOR').click(); // TODO: Replace selector
});

Then('the user should be logged in successfully', () => {
  cy.url().should('not.include', '/login');
  cy.get('YOUR_WELCOME_SELECTOR').should('be.visible'); // TODO: Replace selector
});

Then('the user should be on the product catalog page', () => {
  cy.url().should('include', '/products'); // TODO: Replace URL check
});

// ---------------------
// Scenario: Verify product page details
// ---------------------
When('the user clicks on a product named {string}', (productName) => {
  cy.contains(productName).click(); // TODO: Replace with selector if needed
});

Then('the product page should display the following details:', (dataTable) => {
  const table = dataTable.hashes(); // Convert Cucumber table to array of objects
  table.forEach((row) => {
    switch(row.Field) {
      case 'Image':
        cy.get('YOUR_PRODUCT_IMAGE_SELECTOR').should('be.visible');
        break;
      case 'Description':
        cy.contains(row.ExpectedValue).should('be.visible');
        break;
      case 'Price':
        cy.contains(row.ExpectedValue).should('be.visible');
        break;
      case 'Size Options':
        row.ExpectedValue.split(',').forEach(size => {
          cy.contains(size.trim()).should('exist');
        });
        break;
      case 'Customer Reviews':
        cy.get('YOUR_CUSTOMER_REVIEWS_SELECTOR').should('exist');
        break;
      default:
        cy.log(`Unhandled field: ${row.Field}`);
    }
  });
});

// ---------------------
// Scenario: Add product to wishlist
// ---------------------
Given('the user is on the product page for {string}', (productName) => {
  cy.contains(productName).click(); // TODO: Replace with actual selector
});

When('the user clicks {string}', (buttonName) => {
  cy.contains(buttonName).click(); // TODO: Replace with actual selector
});

Then('the product should be added to the wishlist successfully', () => {
  cy.get('YOUR_WISHLIST_CONFIRM_SELECTOR').should('be.visible');
});

// ---------------------
// Scenario: Add product to cart
// ---------------------
Then('the product should appear in the shopping cart', () => {
  cy.get('YOUR_CART_BUTTON_SELECTOR').click(); // TODO: Replace selector
  cy.get('YOUR_PRODUCT_IN_CART_SELECTOR').should('be.visible');
});

// ---------------------
// Scenario: Verify product availability and stock
// ---------------------
When('the user checks the stock availability', () => {
  cy.get('YOUR_STOCK_STATUS_SELECTOR').should('exist');
});

Then('the available quantity should be displayed correctly', () => {
  cy.get('YOUR_STOCK_STATUS_SELECTOR').invoke('text').should('match', /[0-9]+ available/);
});

