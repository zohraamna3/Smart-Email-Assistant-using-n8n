# Smart Email Classifier & Auto-Responder 📧🤖

An AI-powered automation workflow that reads incoming Gmail messages, classifies them into categories, and takes appropriate actions—auto-reply, draft for review, or ignore—built entirely with free and open-source tools.

---

## Features & What It Does

When a new email arrives in Gmail, this workflow:

1. **Reads Incoming Emails:** Automatically fetches new, unread emails from your inbox.
2. **AI Classification:** Uses Google Gemini API to analyze intent and categorize emails into:
   - **Urgent:** High-priority or time-sensitive messages.
   - **Query:** General questions or information requests.
   - **Complaint:** Negative feedback or support issues.
   - **Spam:** Irrelevant or automated promotional messages.
3. **Smart Action Routing:**
   - **Query** ⚡ → Generates and sends an immediate automatic reply.
   - **Complaint** 📝 → Generates an empathetic reply and saves it as a **Draft** for human review.
   - **Urgent** 📝 → Generates a quick reassuring response and saves it as a **Draft** for rapid approval.
   - **Spam** 🚫 → Ignored automatically (no action taken).

---

## 🛠️ Tech Stack

* **Automation Engine:** [n8n](https://n8n.io) (Self-hosted / Free community version)
* **AI Model:** [Google Gemini API](https://ai.google.dev/) (Free-tier LLM for classification & generation)
* **Email Service:** Gmail API (OAuth 2.0 integration for reading, sending, and drafting)
<img width="1366" height="768" alt="workflow-canvas" src="https://github.com/user-attachments/assets/e5c8ddaf-5f44-4430-8a81-8cdfd5417427" />

---

## ⚙️ How It Works

```text
[ Incoming Email ] 
        │
        ▼
   ( Gmail API )
        │
        ▼
( n8n Trigger Node )
        │
        ▼
( Google Gemini LLM )
  ├── Classifies Email
  └── Generates Response Context
        │
        ▼
   [ Switch Node ]
        ├── Query      ──► [ Gmail API: Send Auto-Reply ]
        ├── Complaint  ──► [ Gmail API: Create Draft ]
        ├── Urgent     ──► [ Gmail API: Create Draft ]
        └── Spam       ──► [ End / No Action ]





