```markdown
# Smart Email Classifier & Auto-Responder

An AI-powered automation workflow that reads incoming Gmail messages, classifies them into categories, and takes the appropriate action — auto-reply, draft for review, or ignore — built entirely with free and open-source tools.

## What It Does

When a new email arrives in Gmail, this workflow:
1. Automatically reads the email
2. Uses AI to classify it as **Urgent**, **Query**, **Complaint**, or **Spam**
3. Routes it through different logic based on category:
   - **Query** → generates and sends an automatic reply
   - **Complaint** → generates an empathetic reply and saves it as a **draft** for human review before sending
   - **Urgent** → generates a reassuring reply and saves it as a **draft** for quick review
   - **Spam** → ignored, no action taken

## Tech Stack

- **[n8n](https://n8n.io)** — open-source workflow automation platform (self-hosted, free)
- **Google Gemini API** — free-tier LLM for email classification and reply generation
- **Gmail API** — for reading emails and creating replies/drafts

## How It Works

```
Gmail Trigger → AI Classification (Gemini) → Switch (routes by category)
                                                  ├── Query → AI Reply → Send Reply
                                                  ├── Complaint → AI Reply → Create Draft
                                                  ├── Urgent → AI Reply → Create Draft
                                                  └── Spam → No Action
```

## Why I Built This

Built as a hands-on project to learn workflow automation, AI agent design, and conditional logic — combining no-code automation with generative AI to solve a real, practical problem (email triage).

## Setup

1. Self-host n8n (`npm install n8n -g` or Docker)
2. Import `smart-email-classifier.json` into your n8n instance
3. Connect your Gmail account (OAuth2 credentials via Google Cloud Console)
4. Add your free Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey)
5. Activate the workflow

## Screenshot

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/d284ec95-a382-4a27-8295-742958b0e9f1" />

