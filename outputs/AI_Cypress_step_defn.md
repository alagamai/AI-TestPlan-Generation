```javascript
import { Given, When, Then } from "cypress-cucumber-preprocessor/steps";

// ---------------------
// Background Steps
// ---------------------
Given('the user has valid login credentials', () => {
  cy.wrap({ email: 'testuser@example.com', password: 'Test@123' }).as('userCredentials');
});

Given('the user is on the login page', () => {
  cy.visit('/login'); // Replace with your login page URL
});

When('the user enters email {string} and password {string}', (email, password) => {
  cy.get('#email').type(email); // Replace '#email' with actual selector
  cy.get('#password').type(password); // Replace '#password' with actual selector
});

When('clicks the Login button', () => {
  cy.get('#loginButton').click(); // Replace with actual login button selector
});

Then('the user should be logged in successfully', () => {
  cy.url().should('not.include', '/login');
  cy.contains('Welcome').should('be.visible'); // Replace 'Welcome' with actual confirmation element
});

Then('the user should be on the product catalog page', () => {
  cy.url().should('include', '/products'); // Replace with actual product catalog page URL
});

// ---------------------
// Scenario: Verify product page details
// ---------------------
When('the user clicks on a product named {string}', (productName) => {
  cy.contains(productName).click(); // Replace with selector if needed
});

Then('the product page should display the following details:', (dataTable) => {
  const table = dataTable.hashes(); // Convert Cucumber table to array of objects
  table.forEach(row => {
    switch(row.Field) {
      case 'Image':
        cy.get('.product-image').should('be.visible'); // Replace selector
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
        cy.get('.customer-reviews').should('exist'); // Replace selector
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
  cy.contains(productName).click();
});

When('the user clicks {string}', (buttonName) => {
  cy.contains(buttonName).click(); // Generic click handler
});

Then('the product should be added to the wishlist successfully', () => {
  cy.contains('Added to Wishlist').should('be.visible'); // Replace with actual message
});

// ---------------------
// Scenario: Add product to cart
// ---------------------
Then('the product should appear in the shopping cart', () => {
  cy.get('#cart').click(); // Open cart
  cy.contains('Summer Breeze Dress').should('exist'); // Verify product is in cart
});

// ---------------------
// Scenario: Verify product availability and stock
// ---------------------
When('the user checks the stock availability', () => {
  cy.get('.stock-status').should('exist'); // Replace with actual selector
});

Then('the available quantity should be displayed correctly', () => {
  cy.get('.stock-status').invoke('text').should('match', /[0-9]+ available/); // Example check
});

