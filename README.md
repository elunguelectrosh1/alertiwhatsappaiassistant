# 🤖 Alerti — WhatsApp Business Automation Platform

**24/7 AI Agent for WhatsApp Business, built by SEEEEOH LABS**

Alerti automates customer responses, order-taking, and appointment booking over WhatsApp for Namibian and SADC SMEs. It's a multi-tenant SaaS platform with a business-owner dashboard and a separate SEEEEOH admin dashboard.

---

## ✨ Features

### For Business Owners
- 📱 **WhatsApp Integration** — connects to the WhatsApp Business Cloud API
- 🤖 **AI-Powered Responses** — automated replies in English, Oshiwambo & Afrikaans
- 📊 **Analytics** — messages, AI response rate, orders taken, response time
- ⚙️ **Configurable** — business hours, welcome message, response language
- 💬 **Message Management** — conversation inbox, with manual takeover from AI

### For SEEEEOH Admins
- 🏢 **Multi-Business Management** — onboard and manage unlimited client businesses
- 💰 **Revenue Dashboard** — MRR, churn, plan breakdown
- 📈 **Platform Analytics** — performance across all businesses

### Demo Business Types
Restaurant 🍔 · Beauty Salon 💅 · Electronics Retail 💻 · Home Services 🔧 — each with its own menu/services, hours, order flow, and pricing, selectable in the built-in WhatsApp simulator.

---

## 💰 Pricing

| Plan | Price | Messages | Numbers | Notes |
|---|---|---|---|---|
| **Starter** | N$500/month | 500/month | 1 | Basic AI responses, email support |
| **Business** | N$1,200/month | 2,000/month | 3 | Advanced AI + training, priority support, analytics |
| **Enterprise** | N$2,500/month | Unlimited | Unlimited | Custom AI model, 24/7 support, API access, custom integrations |

These are the only current, correct figures — this file previously existed as a duplicate copy of the app under the working name **LONGMAL** with different (and internally inconsistent) pricing. That copy has been retired; **Alerti** is the product name going forward.

---

## 🛠️ Tech Stack (current build)

- **Frontend:** HTML5, CSS3, vanilla JavaScript — single static file (`index.html`)
- **Design:** Responsive (one breakpoint at 768px), mobile-first landing page
- **Status:** Front-end demo only — see [Current State](#-current-state--whats-not-real-yet) below

---

## 📦 Quick Deploy (Netlify)

1. Push `index.html` and `ALERTI4.png` to a repo
2. Connect the repo to Netlify
3. Deploy — no build step required for the current static version

---

## ⚠️ Current State — what's not real yet

This build is a strong clickable demo but is **not yet a working product**. Before it's handed to a paying client:

- **No real WhatsApp connection** — the chat is a local JS simulation, not the WhatsApp Cloud API
- **No real AI** — responses are keyword-matched (`menu`, `hour`, `order`, `location`, `price`) against hardcoded text, not a language model. Oshiwambo/Afrikaans responses aren't implemented despite being advertised
- **No persistence** — nothing is saved; "Save Settings" has no handler, chat resets on reload
- **No authentication** — the SEEEEOH admin dashboard (platform revenue, per-client MRR) is reachable from a public button on the landing page, same as the business dashboard
- **All metrics are hardcoded** — message counts, AI response rates, revenue figures are typed into the HTML, not computed

### Roadmap priority order
1. Documentation/pricing cleanup (this file), brand consistency, quick correctness fixes (input escaping, event handling, timezone/hours logic)
2. Database + authentication, so Settings actually saves and each client sees only their own data
3. Real AI agent (LLM-backed, grounded in each business's own menu/hours/pricing) + a working conversation inbox with human takeover
4. WhatsApp Cloud API webhook, then structured order/booking capture
5. Real analytics replacing hardcoded figures, then billing/subscription mechanics

---

## 📞 Contact

Benjamen Elungu — SEEEEOH LABS
+264 85 749 9175
