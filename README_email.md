# AI Email Campaign Automation — n8n + GPT-4o-mini + Gmail

Automatically generates and sends personalized cold emails to every lead in your list. GPT-4o-mini writes a unique email for each prospect based on their company and role — no templates, no copy-paste.

## How It Works

```
Schedule → Google Sheets (leads) → GPT-4o-mini → Gmail → Update Status
```

1. Runs every weekday at 8 AM
2. Reads leads with status "Pending" from Google Sheets
3. GPT-4o-mini writes a unique personalized email per lead
4. Sends via your Gmail account
5. Updates Google Sheets status to "Sent"

## What AI Writes Per Lead

- **Subject line** — curiosity-driven, under 8 words
- **Email body** — 4-5 sentences, mentions their company specifically
- **CTA** — one clear ask (15-min call or reply)
- **Tone** — human, not salesy

## Quick Start

### 1. Set Up Google Sheets

Create a sheet named **Leads** with these columns:
```
First_Name | Last_Name | Email | Company | Role | Industry | Notes | Sender_Name | Product | Status | Subject_Sent | Email_Body | Sent_At
```

Fill in lead data and set `Status` to `Pending`.

### 2. Import Workflow
- Go to your n8n instance
- Click **+** → **Import workflow**
- Upload `ai-email-campaign.json`

### 3. Configure Nodes

**Get Pending Leads & Update Lead Status nodes:**
- Add Google Sheets OAuth2 credential
- Replace `YOUR_GOOGLE_SHEET_ID`

**Generate Personalized Email node:**
- Add OpenAI API key

**Send via Gmail node:**
- Add Gmail OAuth2 credential
- Replace `YOUR_SENDER_NAME` with your name

### 4. Activate
- Toggle workflow to **Active**
- Add leads to Google Sheets with Status = `Pending`

## Google Sheets Example

| First_Name | Last_Name | Email | Company | Role | Industry | Notes | Product | Status |
|------------|-----------|-------|---------|------|----------|-------|---------|--------|
| Sarah | Johnson | sarah@acme.com | Acme Corp | CEO | SaaS | Growing fast, 50 employees | AI automation | Pending |
| Mike | Chen | mike@startup.io | StartupIO | COO | Fintech | Series A funded | AI automation | Pending |

## Best Practices

- Send max 50 emails/day to avoid spam filters
- Use a warmed-up Gmail account
- Fill in `Notes` with specific company info for better personalization
- Review sent emails in Google Sheets before scaling

## Use Cases

- B2B cold outreach for agencies
- SaaS lead generation
- Freelancer client acquisition
- Sales team prospecting automation
- Partnership outreach

## Requirements

- n8n instance (cloud or self-hosted)
- OpenAI API key
- Gmail OAuth2 credentials
- Google Sheets OAuth2 credentials

## Tech Stack

- **n8n** — workflow automation
- **OpenAI GPT-4o-mini** — email personalization
- **Gmail** — email sending
- **Google Sheets** — lead management

---

Built by [Nurmuhammad Adkhamjonov](https://github.com/nurikk-66) — AI Automation Engineer
