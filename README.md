# 🇨🇦 CommonCounsel

**Canada's Business Growth Co-Pilot** CommonCounsel is a comprehensive web platform designed to help Canadian entrepreneurs navigate the complexities of starting, growing, and maintaining a business. It provides personalized regulatory roadmaps, auto-filled legal documents, grant matching, and an AI-powered legal advisor—all at a fraction of the cost of traditional legal counsel.

---

## ✨ Features

* **📍 Personalized Roadmap:** Step-by-step guidance for federal, provincial, and municipal registration based on business type and location.
* **📁 Document Vault:** 12+ pre-filled legal, employment, and operational documents with instant PDF generation.
* **💰 Funding Matcher:** Database of $30B+ in Canadian grants and loans, complete with an eligibility quiz and match scoring.
* **🔔 Compliance Tracker:** Automated timelines for GST/HST filings, business license renewals, and industry-specific requirements.
* **🤖 AI Legal Advisor:** Integrated Claude-powered chat assistant capable of answering Canadian business and compliance questions in real-time.

---

## 🏗️ Project Architecture (Team Modules)

To facilitate parallel development without merge conflicts, the monolithic application was split into 6 distinct modules. Each team member was responsible for a specific domain:

* **`Member-1-Framework.html` (Framework & Styling)**
    * Global HTML `<head>` setup.
    * 600+ lines of pure CSS, including CSS variables, gradients, and custom animations.
    * Custom interactive cursor and scroll reveal observer.
* **`Member-2-Navigation.html` (Routing & Modals)**
    * Sticky navigation bar with scroll state detection.
    * Vanilla JavaScript "router" functions (`gp` for pages, `gs` for scrolling).
    * Dynamic modal overlay system and content configurations.
* **`Member-3-Content.html` (Core Pages & Wizards)**
    * Landing page, features, case studies, and pricing sections.
    * Interactive 5-step Onboarding Wizard.
    * Login/Authentication UI and data capture logic.
* **`Member-4-Documents.html` (Document Engine)**
    * Document Viewer overlay.
    * 12 dynamically pre-filled legal templates (Articles of Incorporation, NDA, WSIB Registration, etc.).
    * In-browser HTML-to-PDF compilation logic.
* **`Member-5-Grants.html` (Grants & Dashboard)**
    * Funding database UI and filtering logic.
    * Interactive Eligibility Quiz with dynamic match scoring.
    * User Dashboard featuring the roadmap timeline, compliance calendar, and document mini-vault.
* **`Member-6-AI.html` (Claude AI Assistant)**
    * Anthropic API integration (`claude-3-5-sonnet`).
    * Floating global sidebar chat and dedicated dashboard AI tab.
    * Dynamic system prompt generation based on the user's business profile.

---

## 🚀 Setup & Assembly Instructions

Because this project was built using **Vanilla HTML, CSS, and JavaScript** (Option B), there is no complex build pipeline (no Webpack, Node.js, or NPM required). 

To assemble the final working prototype:

1.  **Create an `index.html` file.**
2.  **Stack the Modules:** Copy and paste the contents of each Member's file into `index.html` in the following order to ensure proper DOM rendering and script execution:
    * *First:* `Member-1-Framework.html` (Provides the `<head>`, `<style>`, and opening `<body>` tags).
    * *Second:* `Member-2-Navigation.html` (Navbar and Modals).
    * *Third:* `Member-3-Content.html` (Home, Onboarding, Login).
    * *Fourth:* `Member-4-Documents.html` (Document Vault overlay).
    * *Fifth:* `Member-5-Grants.html` (Grants, Eligibility, and Dashboard).
    * *Sixth:* `Member-6-AI.html` (AI Chat and closing `</body></html>` tags).
3.  **Run Locally:** Open `index.html` directly in any modern web browser. No local server is strictly required, though using a tool like VS Code's *Live Server* is recommended.

---

## 🔑 Configuration (AI Integration)

To enable the AI Legal Advisor (Member 6's contribution), you must provide a valid Anthropic API key.

1. Locate the `fetch('https://api.anthropic.com/v1/messages', {...})` calls inside `Member-6-AI.html`.
2. Add your API key to the headers:
   ```javascript
   headers: {
     'Content-Type': 'application/json',
     'x-api-key': 'YOUR_ANTHROPIC_API_KEY_HERE',
     'Anthropic-Version': '2023-06-01',
     'anthropic-dangerous-direct-browser-access': 'true'
   }
