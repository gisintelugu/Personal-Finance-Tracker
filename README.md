# Personal Finance Tracker

A single-page, Google Sheets-backed personal finance tracker. Each user signs in with Google and connects their own spreadsheet or creates a new one. The app does not send financial records to a separate application server.

## Current capabilities

- Multiple bank accounts and opening balances
- Income and expense transactions
- Transfers between accounts (paired transfer-in / transfer-out rows; excluded from income and expense totals)
- EMI and recurring expense plans
- Manual payment confirmation, with a transaction recorded in the selected account
- Dashboard totals, account balances, payment reminders, and basic transaction filters

## Setup

1. In Google Cloud Console, select your project and enable **Google Sheets API**.
2. Configure **Google Auth Platform**. For initial testing, use **External** audience and add your Google account under **Test users**.
3. Create an OAuth client of type **Web application**.
4. Add this Authorized JavaScript origin:
   `https://gisintelugu.github.io`
5. Set the OAuth Client ID in the `CLIENT_ID` constant near the bottom of `index.html`.
6. Deploy this repository using GitHub Pages: **Settings → Pages → Deploy from a branch → main → / (root)**.

The OAuth consent configuration and Google API enablement are required even when the site is hosted by GitHub Pages. During OAuth testing, only configured test users can sign in. A public release may require completing Google's OAuth verification requirements for the requested Sheets scope.

## Data and privacy

The app accesses Google Sheets using the signed-in user's OAuth access token. Tokens remain in page memory and are not written to local storage. The Sheets API scope currently requested is `https://www.googleapis.com/auth/spreadsheets`; this is broad spreadsheet access for the signed-in user. Users should connect only spreadsheets they intend this app to read and update.

The repository is public, so never commit OAuth client secrets, bank credentials, or personal financial data. The OAuth Client ID is a public identifier; it is not a secret.

## Important status

This is an early GitHub Pages port. Test with a **new, empty spreadsheet** first. Existing spreadsheets must use the exact four sheet names and column order created by the app: `Accounts`, `Transactions`, `Fixed Expenses`, and `Dashboard Summary`.

The current page includes core create/read workflows. Transaction editing/deletion, account editing, advanced date sorting, and comprehensive analytics are not yet implemented in this static version. Verify all data changes against the Google Sheet before using it for important financial records.
