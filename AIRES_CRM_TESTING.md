# Testing Agent Overview

This repository demonstrates an automated front-end testing setup that leverages OpenAI's **Computer Use Assistant (CUA)** model. The project is composed of three separate apps:

1. **frontend/** – A Next.js UI where you define test cases and watch them execute in real time.
2. **cua-server/** – A Node service that communicates with the CUA model and uses Playwright to control a browser session.
3. **sample-test-app/** – A demo e-commerce site provided as a default target for automated tests.

Together these apps allow you to describe browser actions (e.g. clicking buttons or entering text) and let the CUA model perform those actions automatically. The server relays updates back to the frontend so you can observe progress and results.

## Running the Demo

1. Clone this repository and install dependencies using `npm install` at the repo root.
2. Create `.env.development` files in each subdirectory and supply your `OPENAI_API_KEY` (and sample-app credentials).
3. Run `npx playwright install` and start all apps with `npm run dev`.
4. Visit `http://localhost:3000` to access the UI. From there you can trigger the predefined test flow against the sample store running on port `3005`.

See the individual READMEs for more details on configuration.

## Adapting for Aires CRM

To test a different web application such as **Aires CRM** located at `https://aires-staging.vercel.app`, point the testing agent toward that URL and write test cases describing the desired actions. In the UI you can set the app URL and provide any required login credentials. The CUA model will then execute those tests in a browser just as it does for the sample e-commerce app.

A typical workflow for testing Aires CRM would be:

1. Open the frontend UI and change the target URL to the CRM staging site.
2. List the steps of your test scenario, such as logging in, navigating to customer records, creating new contacts, or generating reports.
3. Start the test run. The cua-server launches a Playwright browser, the CUA model follows your instructions, and you watch the progress from the UI.
4. Review the results and logs to confirm that the expected behaviors occurred.

You can customize the prompts to cover various user roles, from basic login tests to more complex workflows (e.g. contact management, inventory handling, or reporting) like those outlined in the test plan above.

## PXP ReactJS Admin - Comprehensive Q/A Test List

### 1. Authentication & Login Tests
- **Test 1.1: Sales Rep Login** – Verify Sales Rep can log in and access the dashboard
- **Test 1.2: Admin Login** – Verify Admin can log in and access the admin dashboard
- **Test 1.3: Invalid Login** – Verify invalid credentials show an error

### 2. Contact Management Tests
- **Test 2.1: Create New Buyer Contact**
- **Test 2.2: Create New Broker Contact**
- **Test 2.3: Edit Existing Contact**
- **Test 2.4: Delete Contact**
- **Test 2.5: Search and Filter Contacts**
- **Test 2.6: Bulk Contact Import**

### 3. Inventory Management Tests
- **Test 3.1: View Unit Inventory**
- **Test 3.2: Edit Unit Information**
- **Test 3.3: Add New Unit**
- **Test 3.4: Manage Parking Inventory**
- **Test 3.5: Manage Storage Inventory**

### 4. Dashboard & Reporting Tests
- **Test 4.1: Sales Rep Dashboard**
- **Test 4.2: Admin Dashboard**
- **Test 4.3: Sales Reports**
- **Test 4.4: Contact Reports**

### 5. Email & Communication Tests
- **Test 5.1: Send Individual Email**
- **Test 5.2: Email Campaign Creation**
- **Test 5.3: Email Template Management**
- **Test 5.4: Email Inbox Management**

### 6. User Management Tests (Admin Only)
- **Test 6.1: Create New Sales Rep**
- **Test 6.2: Edit User Permissions**
- **Test 6.3: Delete User**

### 7. Project Management Tests
- **Test 7.1: View Project Details**
- **Test 7.2: Edit Project Information**

### 8. Advanced Features Tests
- **Test 8.1: Contract Signing**
- **Test 8.2: Meeting Scheduling**
- **Test 8.3: Task Management**

### 9. Mobile Responsiveness Tests
- **Test 9.1: Mobile Dashboard**
- **Test 9.2: Mobile Contact Management**

### 10. Performance & Error Handling Tests
- **Test 10.1: Large Data Set Handling**
- **Test 10.2: Error Handling**

These scenarios can be used as prompts for the CUA-powered test agent. Set the app URL to `https://aires-staging.vercel.app` in the frontend UI and run each test individually to verify functionality.
