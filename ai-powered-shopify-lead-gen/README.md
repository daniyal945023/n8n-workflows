# AI Lead Generation & Automated Outreach Workflow (n8n)

Finding qualified e-commerce leads, analyzing their tech stacks, traffic, and revenue, and manually drafting personalized emails eats up days of valuable sales time. Traditional static lead lists are usually outdated, and generic templates fail to convert.

This production-ready **n8n AI Lead Generation & Outreach Engine** solves that bottleneck by fully automating the pipeline. It scrapes targeted Shopify stores, extracts deep store insights using Google Gemini AI, drafts context-aware hyper-personalized emails based on your chosen tone, and manages CRM tracking in real-time—all on autopilot.

---

## Key Features

* **Interactive Form Trigger:** Captures campaign parameters instantly, including business type, target location, lead volume, and preferred email style (**Friendly**, **Professional**, **Simple**).
* **Automated Shopify Scraping:** Leverages Apify actors to pull targeted store data and filters out entries missing valid website URLs.
* **Store Intelligence & AI Summaries:** Extracts tech stacks, traffic estimates, and promo data via Apify, then uses Google Gemini to generate concise company summaries.
* **CRM Logging:** Automatically appends all enriched leads and insights to a Google Sheets document with a `Pending` mailing status.
* **Personalized AI Outreach:** Sequentially loops through leads, drafts contextualized cold outreach emails using Gemini structured JSON outputs, and dispatches them via Gmail.
* **Status Tracking:** Automatically updates the Google Sheets tracker to `✅` once an email has been successfully sent.

---

## Workflow Architecture

1. **On form submission:** User specifies campaign parameters via an n8n form.
2. **Scrape Shopify Store Leads (Apify):** Queries and retrieves matching Shopify stores.
3. **FilterByWebsite:** Discards entries lacking a valid web presence.
4. **Analyze Shopify Store Data (Apify):** Deep-crawls tech stack, traffic, and revenue indicators.
5. **Format Facts with LLM (Google Gemini):** Synthesizes raw data points into structured company overviews.
6. **Append row in sheet:** Saves initial lead data to Google Sheets as `Pending`.
7. **Loop Over Items & Wait:** Batch-processes leads safely.
8. **Send Emails with AI & Send a message (Gmail):** Generates personalized cold copy and executes outreach.
9. **Append or update row in sheet:** Marks the outreach status as complete (`✅`).

---

## Prerequisites & Credentials

To deploy this workflow, ensure you have active credentials configured in your n8n instance for:

* **Google Gemini (PaLM) API**
* **Apify API Token**
* **Google Sheets OAuth2 API**
* **Gmail OAuth2 Account**

---

## Setup Instructions

1. Import the provided workflow JSON file into your n8n environment.
2. Connect your respective credentials for Google Gemini, Apify, Google Sheets, and Gmail.
3. Open the **Append row in sheet** and **Append or update row in sheet** nodes, and update the `documentId` and `sheetName` fields to point to your target spreadsheet.
4. Execute the workflow or activate the form trigger to begin generating leads and launching personalized campaigns.
