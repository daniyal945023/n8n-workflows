# AI Front Desk Automation

Local service businesses (dental, medspa, HVAC, legal, real estate) lose 20–30% of inbound calls. This system answers calls via AI, checks real calendar availability, books appointments, syncs to CRM, and recovers missed calls via SMS.

This folder contains a suite of n8n workflows that power an automated AI Front Desk. The system manages call outcomes, synchronizes contact data with a CRM, attempts automatic SMS recovery for missed calls, and provides real-time error monitoring to ensure maximum uptime.

## Included Workflows

* **Call Processing & Missed Call Recovery:** Captures end-of-call webhooks from the AI voice assistant (Vapi), parses the call outcome (booked, inquiry, or missed), searches for or creates the contact in HubSpot, logs the interaction, and automatically dispatches a recovery SMS via TextBelt if the call was missed.
* **Error Monitoring & Alerting:** Acts as a global fallback for the system. Uses the n8n Error Trigger to catch any failed node executions and immediately routes diagnostic alerts (including workflow name and error message) to a designated Slack channel.
* **Core Front Desk Operations:** Handles the primary data routing, internal syncing, or scheduling logic for the AI assistant. *(Note: Adjust this bullet point to match the specific function of your third workflow).*

## Prerequisites

To utilize these workflows, you need active accounts and API credentials for the following services:

* **n8n:** Cloud or self-hosted instance (Version 1.0+)
* **Vapi:** For AI voice generation and call state webhooks
* **HubSpot CRM:** For contact management and call logging
* **TextBelt:** For automated SMS dispatch(for testing only). For Production, use Twilio.
* **Slack:** For developer/admin error notifications

## Installation & Setup

1. **Import Workflows:** In your n8n workspace, go to **Workflows** > **Add Workflow** > click the menu icon in the top right > **Import from File**. Import the JSON files from this folder.
2. **Configure Credentials:** Open each workflow and update the credential nodes. You will need to input your Vapi Shared Secret, HubSpot Header Auth token, TextBelt API key, and Slack OAuth token.
3. **Update Placeholders:** Scan the nodes for placeholder strings generated during sanitization (e.g., `YOUR_WEBHOOK_ID_HERE`, `YOUR_SLACK_USER_ID`, `YOUR_SLACK_USERNAME`) and replace them with your actual environment variables or IDs.
4. **Activate:** Toggle the workflows to **Active** to begin listening for incoming webhooks and global errors.
