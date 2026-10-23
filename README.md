H&M Sale Tracker & Price Monitor

An n8n automation workflow that retrieves H&M sale-page HTML through Browserless, extracts product information, filters duplicate URLs, and syncs records to Google Sheets.
Important: This is a learning/portfolio project. Website markup and access rules can change, so selectors and price extraction may need maintenance. Verify the output before relying on it.

Workflow

Schedule Trigger → HTTP Request (Browserless) → HTML extraction → Code in JavaScript → Remove Duplicates → Google Sheets
Features
- Runs on a scheduled interval (configured for every 30 minutes).
- Requests the H&M UK ladies’ sale page through Browserless.
- Extracts product data from the returned page HTML.
- Uses product URL as the deduplication/matching key.
- Sends product rows to Google Sheets.

  
Data fields

The Google Sheet is expected to have these header names in its first row:
- Product names
- Percentage Off
- Price Before
- Price After
- Url

  
Setup

1. Import hm-sale-tracker.json into your n8n instance.
2. In the HTTP Request node, replace YOUR_BROWSERLESS_TOKEN with your own Browserless token. Prefer storing secrets in n8n credentials or environment variables where supported, rather than committing them to the workflow file.
3. Connect your own Google Sheets account in the Google Sheets node.
4. Select your spreadsheet and worksheet, and verify that the headers match the fields above.
5. Execute the workflow manually and inspect the output of the HTML and Code nodes. Confirm that product names, URLs, original prices, sale prices, and discounts are populated correctly.
6. Activate the workflow only after testing.


   
Security

- Never commit API tokens, OAuth credentials, cookies, or private spreadsheet data.
- The workflow JSON in this repository uses a placeholder token. Add your own secret inside n8n after importing.
- If a real token was previously shared publicly or included in a public file, revoke it and generate a replacement.
  
Limitations

- The workflow depends on the current HTML structure of H&M’s website; selectors may stop matching after a site update.
  
- Product availability, prices, and discount labels should be validated against the live product page. Do not assume a missing original price can be inferred reliably.
  
- Browserless usage is subject to the provider’s plan and limits.
  
- Respect the website’s terms, robots directives, and applicable laws; use reasonable request frequency.

  
Built with

- n8n
- Browserless
- Google Sheets

  
License

Choose a license before publishing. If you want others to reuse the code, MIT is a common permissive option; make sure the project’s use of third-party services and website content is compatible with your intended license.
