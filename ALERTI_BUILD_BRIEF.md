# Alerti — Build Brief for a New Complete Site

**Product:** Alerti — 24/7 WhatsApp AI agent for SMEs
**Built by:** SEEEEOH LABS (Benjamen Elungu, Windhoek, Namibia)
**Market:** SMEs across Namibia and the SADC region

This is the consolidated spec to hand to a developer (human or AI) building the real, production version — combining what exists today, what it needs to become, and the business context around it.

---

## 1. What the product is

A multi-tenant WhatsApp automation SaaS with two user types:

- **Business owners** — get a dashboard (Overview, Messages, WhatsApp Demo, Settings, Billing) to manage their own AI agent
- **SEEEEOH admins** — get a separate dashboard (Platform Overview, All Businesses, Revenue, Analytics) to manage all client businesses

The core value proposition: a business's WhatsApp number is connected to an AI agent that answers customer questions (menu/services, hours, location, pricing), takes orders/bookings, and responds in English, Oshiwambo, and Afrikaans — 24/7, without a human.

## 2. What exists today (`index.html`, included alongside this brief)

A single static HTML/CSS/JS file — no backend, no database, no real WhatsApp connection. It's a strong clickable **demo**, not a working product:

- Chat is a local JS simulation; "AI" is 6 keyword branches (`menu`, `hour`, `order`, `location`, `price`) over 4 hardcoded business types (restaurant, salon, electronics retail, home services)
- Every dashboard metric (247 messages, 94% AI rate, 43 orders, N$54,300 revenue, 47 businesses, etc.) is typed directly into the HTML — not computed
- Nothing persists: "Save Settings" has no handler; chat resets on reload
- No authentication — both dashboards, including platform revenue and per-client MRR, open from public buttons on the landing page
- No real multilingual support despite the language selector existing in Settings

## 3. What the new site needs to actually do

**Real backend & data**
- Database (businesses, conversations, messages, settings, orders, subscriptions)
- Authentication with tenant separation — business owners see only their own data; admin view sits behind a separate role check
- Settings that actually save

**Real AI agent**
- LLM-backed responses (not keyword matching), grounded in each business's own menu/hours/location/pricing so answers aren't invented
- Genuine English/Oshiwambo/Afrikaans support, tied to the language selector

**Real WhatsApp connection**
- WhatsApp Cloud API: webhook verification (GET) + inbound message handling with replies via the Graph API
- Access tokens and phone-number ID in environment variables, never in the page

**Real conversation management**
- A working Messages inbox: threads, unread indicators, full history
- A "take over from AI" control to pause automation and hand a conversation to a human — this is the feature most likely to come up in a sales meeting
- Orders/bookings captured as structured records, with confirmation to the customer and a notification to the owner (not just a chat reply that goes nowhere)

**Real analytics**
- Dashboard numbers computed from actual data, replacing the hardcoded figures

**Quality/correctness (carry over from current build, fix in the rebuild)**
- Escape user input in chat (currently vulnerable to script injection via `innerHTML`)
- Compute "open now" from actual business hours instead of hardcoding "We're currently OPEN!"
- Locale-appropriate time formatting (24-hour, not `en-US` AM/PM)
- Accessibility: keyboard-navigable nav (currently `<div onclick>`), labelled form inputs, live region for chat
- Responsive beyond the single 768px breakpoint
- Link preview metadata (Open Graph tags, favicon) — this product is shared via WhatsApp links and currently has none
- Lead capture form on the landing page — currently both CTAs go straight to demos with no way for an interested owner to leave contact info

## 4. Pricing (current, confirmed — carry forward as-is)

| Plan | Price | Messages | Numbers |
|---|---|---|---|
| Starter | N$500/month | 500/month | 1 |
| Business | N$1,200/month | 2,000/month | 3 |
| Enterprise | N$2,500/month | Unlimited | Unlimited |

## 5. Demo business types to preserve/extend

Restaurant 🍔 · Beauty Salon 💅 · Electronics Retail 💻 · Home Services 🔧 — each needs its own menu/services, hours, order flow, location, and pricing, same structure as the current demo but backed by real per-business configuration instead of hardcoded objects.

## 6. Suggested build order

1. Auth + database schema, so the dashboards have somewhere real to read/write
2. LLM-backed agent (grounded in per-business data) + real conversation inbox with human takeover
3. WhatsApp Cloud API webhook, then structured order/booking capture
4. Real analytics, then billing/subscription mechanics
5. Landing page polish — lead capture form, link preview metadata, "how it works" section, a hard-question demo prompt to show graceful fallback to human handoff

---

**Contact:** Benjamen Elungu, SEEEEOH LABS — +264 85 749 9175
