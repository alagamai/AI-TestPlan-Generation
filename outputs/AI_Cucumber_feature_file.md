Feature: End-to-End User Journey for Style Haven

  Background: 
    # End-to-End setup
    Given the user navigates to the Style Haven homepage
    And the user is not logged in

  # User Accounts Scenarios
  Scenario: User Registration
    # End-to-End
    Given the user is on the registration page
    When the user enters name "Test User", email "testuser@example.com", and password "Test@123"
    And clicks the Register button
    Then the user should be registered successfully
    And redirected to the login page

  Scenario: User Login with Valid Credentials
    # End-to-End
    Given the user is on the login page
    When the user enters email "testuser@example.com" and password "Test@123"
    And clicks the Login button
    Then the user should be logged in successfully
    And redirected to the homepage

  Scenario: Profile Update
    # Integration
    Given the user is logged in
    When the user navigates to the profile page
    And updates the address to "123 Street, Springfield" and phone to "9876543210"
    Then the profile should be updated successfully
    And a confirmation message should be displayed

  # Product Catalog Scenarios
  Scenario: Browse Products by Category
    # End-to-End
    Given the user is logged in
    When the user clicks on the category "Women’s Dresses"
    Then all products under the selected category should be displayed

  Scenario: Search for a Product
    # Integration
    Given the user is logged in
    When the user searches for "Trendy Dress"
    Then the relevant products should be displayed

  Scenario: View Product Details
    # End-to-End
    Given the user is logged in
    When the user clicks on a product with ID "101"
    Then the product detail page should display description, images, size chart, and reviews

  Scenario: Add Product to Wishlist
    # Integration
    Given the user is logged in
    When the user clicks "Add to Wishlist" on product with ID "101"
    Then the product should be added to the wishlist successfully

  # Cart Scenarios
  Scenario: Add Product to Cart
    # End-to-End
    Given the user is logged in
    When the user adds product with ID "101" to the cart
    Then the product should appear in the cart

  Scenario: Remove Product from Cart
    # Integration
    Given the user has product with ID "101" in the cart
    When the user removes the product
    Then the product should no longer appear in the cart

  Scenario: Update Product Quantity in Cart
    # Integration
    Given the user has product with ID "101" in the cart
    When the user updates the quantity to "2"
    Then the cart total should reflect the updated quantity

  # Checkout Scenarios
  Scenario: Checkout with Items in Cart
    # End-to-End
    Given the user has products with IDs "101,102" in the cart
    When the user proceeds to checkout
    And enters shipping address "123 Street, Springfield" and payment details "Credit Card 4111111111111111"
    And places the order
    Then the order should be placed successfully
    And a confirmation email should be sent

  Scenario: Checkout with Empty Cart
    # End-to-End
    Given the user has no products in the cart
    When the user attempts to checkout
    Then an error message "Cart is empty" should be displayed

  Scenario: Checkout with Invalid Payment
    # Integration
    Given the user has products with IDs "101,102" in the cart
    When the user enters invalid payment details "1234567890123456"
    And attempts to place the order
    Then an error message "Payment failed" should be displayed

  # Seller Dashboard Scenarios
  Scenario: Add New Product as Seller
    # End-to-End
    Given the user is logged in as a seller with email "seller@example.com" and password "Seller@123"
    When the seller navigates to the dashboard and adds a new product "Trendy Dress" priced "49.99"
    Then the product should appear in the seller inventory

  Scenario: Update Product Inventory
    # Integration
    Given the seller has product with ID "101" in inventory
    When the seller updates the quantity to "20"
    Then the inventory should be updated accordingly

  Scenario: Delete Product from Inventory
    # Integration
    Given the seller has product with ID "102" in inventory
    When the seller deletes the product
    Then the product should be removed from inventory

  Scenario: View Orders in Seller Dashboard
    # Integration
    Given the seller has orders placed by users
    When the seller navigates to Orders
    Then all orders should be displayed with correct details

  Scenario: Generate Sales Report
    # Integration
    Given the seller is on the dashboard
    When the seller clicks on Sales Report
    Then a sales report for the selected period should be generated

  # Combined E2E Scenario
  Scenario: Complete End-to-End Flow from Registration to Checkout
    # End-to-End
    Given a new user registers with name "New User", email "newuser@example.com", and password "NewPass@123"
    And logs in successfully
    When the user browses products in "Women’s Dresses"
    And searches for "Trendy Dress"
    And views product with ID "101" details
    And adds the product to the cart
    And proceeds to checkout with shipping address "456 Elm Street, Springfield" and payment "Credit Card 4111111111111111"
    Then the order should be placed successfully
    And a confirmation email should be received

