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
