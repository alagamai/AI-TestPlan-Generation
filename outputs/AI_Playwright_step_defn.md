import { Given, When, Then } from '@cucumber/cucumber';
import { expect, Page } from '@playwright/test';

let page: Page;

// ---------------------
// Background Steps
// ---------------------
Given('the user has valid login credentials', async function () {
  this.userCredentials = { email: 'testuser@example.com', password: 'Test@123' };
});

Given('the user is on the login page', async function () {
  page = this.page;
  await page.goto('/login'); // Replace with your login page URL
});

When('the user enters email {string} and password {string}', async function (email, password) {
  await page.fill('#email', email); // Replace with actual selector
  await page.fill('#password', password); // Replace with actual selector
});

When('clicks the Login button', async function () {
  await page.click('#loginButton'); // Replace with actual selector
});

Then('the user should be logged in successfully', async function () {
  await expect(page).not.toHaveURL(/\/login/);
  await expect(page.locator('text=Welcome')).toBeVisible(); // Replace with actual confirmation element
});

Then('the user should be on the product catalog page', async function () {
  await expect(page).toHaveURL(/\/products/); // Replace with actual product catalog URL
});

// ---------------------
// Scenario: Verify product page details
// ---------------------
When('the user clicks on a product named {string}', async function (productName) {
  await page.click(`text=${productName}`); // Replace with specific selector if needed
});

Then('the product page should display the following details:', async function (dataTable) {
  const table = dataTable.hashes(); // Convert Cucumber table to array of objects
  for (const row of table) {
    switch (row.Field) {
      case 'Image':
        await expect(page.locator('.product-image')).toBeVisible(); // Replace selector
        break;
      case 'Description':
        await expect(page.locator('.product-description')).toHaveText(row.ExpectedValue);
        break;
      case 'Price':
        await expect(page.locator('.product-price')).toHaveText(row.ExpectedValue);
        break;
      case 'Size Options':
        const sizes = row.ExpectedValue.split(',');
        for (const size of sizes) {
          await expect(page.locator(`text=${size.trim()}`)).toBeVisible();
        }
        break;
      case 'Customer Reviews':
        await expect(page.locator('.customer-reviews')).toBeVisible(); // Replace selector
        break;
      default:
        console.warn(`Unhandled field: ${row.Field}`);
    }
  }
});

// ---------------------
// Scenario: Add product to wishlist
// ---------------------
Given('the user is on the product page for {string}', async function (productName) {
  await page.click(`text=${productName}`);
});

When('the user clicks {string}', async function (buttonName) {
  await page.click(`text=${buttonName}`);
});

Then('the product should be added to the wishlist successfully', async function () {
  await expect(page.locator('text=Added to Wishlist')).toBeVisible(); // Replace with actual message
});

// ---------------------
// Scenario: Add product to cart
// ---------------------
Then('the product should appear in the shopping cart', async function () {
  await page.click('#cart'); // Open cart
  await expect(page.locator('text=Summer Breeze Dress')).toBeVisible(); // Verify product in cart
});

// ---------------------
// Scenario: Verify product availability and stock
// ---------------------
When('the user checks the stock availability', async function () {
  await expect(page.locator('.stock-status')).toBeVisible(); // Replace selector
});

Then('the available quantity should be displayed correctly', async function () {
  const text = await page.locator('.stock-status').innerText();
  expect(text).toMatch(/[0-9]+ available/); // Example check
});

