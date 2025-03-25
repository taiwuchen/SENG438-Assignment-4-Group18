**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group \#:      |     |
| -------------- | --- |
| Student Names: |     |
|                |     |
|                |     |
|                |     |

# Introduction


# Analysis of 10 Mutants of the Range class 

# Report all the statistics and the mutation score for each test class



# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process

## a. Identify Functionalities

First, we explored the **Gap Canada website** to find key user flows. We selected two major functionalities:

- **User Account Management** (e.g., Login)
- **Shopping Process** (e.g., Search, Add to Cart)

---

## b. Define Specific Test Scenarios

Within these functionalities, we broke down test scenarios to cover both positive and negative flows, as well as various data inputs.

---

## c. Outline Test Steps and Expected Results

For each scenario, we created step-by-step instructions describing how to navigate the site, what inputs to provide, and the expected outcome, such as:

- **Positive Scenario**:  
  - *Expected Result*: "Login succeeds and displays a welcome message."
  
- **Negative Scenario**:  
  - *Expected Result*: "An error message appears for invalid credentials."

---

## d. Record and Fine-Tune in Selenium IDE

We recorded the steps using **Selenium IDE** and performed the following tasks:

1. Added necessary waits or adjusted locators (CSS/XPath) to ensure that each step interacts with the correct element.
2. Included verification commands (assertions) to confirm that the actual results match the expected results.

---

## e. Example of 8 Test Cases

### **Login Functionality**
| Test Case ID | Test Scenario                         | Expected Outcome                                 |
|-------------|---------------------------------------|--------------------------------------------------|
| TC1         | Valid Login                            | Login succeeds and displays a welcome message     |
| TC2         | Invalid Login (wrong password)          | Error message appears indicating invalid password |
| TC3         | Invalid Login (unregistered email)      | Error message appears indicating invalid email    |
| TC4         | Logout                  | Successfully logs out and redirects to home page  |

### **Shopping Functionality**
| Test Case ID | Test Scenario                         | Expected Outcome                                 |
|-------------|---------------------------------------|--------------------------------------------------|
| TC5         | Search for an Existing Product          | Displays product search results                   |
| TC6         | Search for a Non-Existing Product       | Displays "No results found" message                |
| TC7         | Add Product to Cart                     | Product added successfully with confirmation       |
| TC8         | Remove Product from Cart                 | Product removed from cart with confirmation        |

---



# Explain the use of assertions and checkpoints

## a. Purpose of Assertions

Assertions verify whether the application is functioning as expected after each significant action. They ensure that:

- The application behaves as intended.
- Expected outcomes match actual outcomes.
- Any discrepancies are immediately detected.

**Example:**  
After clicking the **“Login”** button, we use an assertion to check if the page displays a **“Welcome”** message or the user’s account dashboard.

---

## b. Types of Assertions in Selenium IDE

Selenium IDE provides various assertion commands to verify different aspects of the application. The most commonly used ones are:

- **assertText:**  
  Checks if specific text appears on the page.  
  *Example:* Verifying the message **“Login successful”** after signing in.

- **assertElementPresent:**  
  Verifies whether a certain element (e.g., a **“Sign Out”** link) is present in the DOM.  
  *Example:* Checking the presence of the **“Logout”** button after a successful login.

- **verifyTitle:**  
  Confirms that the page title matches the expected title.  
  *Example:* Ensuring that the title changes to **“My Account”** after logging in.

---

## c. Strategic Checkpoints

To ensure robustness, we place assertions strategically throughout the test scripts:

### Before Key Actions:
- **Purpose:** To confirm that critical elements are loaded and ready.  
- *Example:* Check that the **search bar** is present before entering any query.

### After Key Actions:
- **Purpose:** To verify that the result or outcome of the action matches expectations.  
- *Example:* Confirm that a **“Product added to cart”** notification appears after adding an item.

---

## d. Example of Assertion Usage

### **TC1: Valid Login**
- **Step:** Submit valid credentials.
- **Assertion:**  
  - Use **assertText** to check for the message **"Welcome, [User Name]"**.  
  - Validate that the **user dashboard** is displayed.

### **TC5: Search for an Existing Product**
- **Step:** Type a product name in the search bar and submit.  
- **Assertion:**  
  - Use **assertElementPresent** to ensure that **search results** are displayed.  
  - Optionally, use **assertText** to verify the presence of the product name in the results list.



# how did you test each functionaity with different test data

| **Test Case**                           | **Test Data**                                                                                                                                      | **Expected Outcome**                                                              |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| **1. Valid Login**                      | Email: evanchaaan@gmail.com<br>Password: $K^&NBj0jXtP                                                                                                | Successful login; welcome message (e.g., "Welcome, validuser") is displayed         |
| **2. Invalid Login (Wrong Password)**   | Email: evanchaaan@gmail.com<br>Password: WrongPass                                                                                                | Error message: "Your password is incorrect" is displayed                           |
| **3. Invalid Login (Unregistered Email)** | Email: none@test.com<br>Password: AnyPassword                                                                                               | Error message: "Email not recognized" (or similar) is displayed                    |
| **4. Logout**                           | Start with a valid logged-in session, then click on the Logout/Sign Out link                                                                      | Returns to guest state; Sign In link is visible                                  |
| **5. Search for Existing Product**      | Search term: "Jersey Crewneck T-Shirt"                                                                                                                    | Search results display relevant products                                          |
| **6. Search for Non-Existing Product**  | Search term: "XYZ123"                                                                                                                                | "No results found" message is displayed                                          |
| **7. Add Product to Cart**              | After searching for a product (e.g., "Jeans"), select a product and choose options (size, color) if required, then click "Add to Cart"            | The product is added to the cart; cart badge or confirmation is updated             |
| **8. Remove Product from Cart**         | With a product already in the cart, click the "Remove" or "Delete" option for the product                                                           | The product is removed; cart updates to show zero items or "Your cart is empty"     |



# Discuss advantages and disadvantages of Selenium vs. Sikulix


| **Tool**   | **Advantages**                                                                                                        | **Disadvantages**                                                                                                                              |
|-----------|------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Selenium  | - Specialized for web applications, allowing direct interaction with HTML elements (DOM).                                | - Limited to browser-based testing (not ideal for desktop apps).                                                                                 |
|           | - Easy record-and-playback for quick test script creation.                                                               | - Dynamic web elements may require frequent locator updates.                                                                                     |
|           | - Built-in assertions for validation.                                                                                    | - No direct visual testing (relies on DOM locators rather than image matching).                                                                   |
| Sikulix   | - Uses image recognition, enabling automation of any on-screen elements (including desktop apps).                        | - Highly sensitive to UI changes (small design alterations can break tests).                                                                     |
|           | - Cross-platform support (Windows, macOS, Linux).                                                                        | - Slower and more resource-intensive due to image processing.                                                                                   |
|           | - Simple scripting if you’re comfortable with visual matching.                                                           | - Lacks built-in web-specific features (treats browser as just another window).                                                                  |

---



# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
