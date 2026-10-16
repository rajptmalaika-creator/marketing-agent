# 🍽️ BistroPulse — Complete System Documentation & Technical Manual

> **BistroPulse: The AI Omnichannel Marketing & Value Positioning Automation Hub for Local Independent Restaurants**

---

## 📑 Complete Documentation Index

This single comprehensive manual compiles all documentation for BistroPulse:
1. **[System Overview & Architecture](#part-1-system-overview--architecture)**
2. **[The Value Positioning Playbook ("Position Their Value")](#part-2-the-value-positioning-playbook)**
3. **[WhatsApp Marketing & Concierge Automation](#part-3-whatsapp-marketing--concierge-automation)**
4. **[Instagram & Facebook Marketing Automation](#part-4-instagram--facebook-marketing-automation)**
5. **[Omnichannel Campaign Studio & Calendar](#part-5-omnichannel-campaign-studio--calendar)**
6. **[VIP Diners CRM & Loyalty System](#part-6-vip-diners-crm--loyalty-system)**
7. **[Complete REST API Reference](#part-7-complete-rest-api-reference)**
8. **[Meta Graph API & WhatsApp Cloud API Setup Guide](#part-8-meta-graph-api--whatsapp-cloud-api-setup-guide)**
9. **[Quick Start, Installation & Deployment](#part-9-quick-start-installation--deployment)**

---

## Part 1: System Overview & Architecture

BistroPulse is an application engineered specifically for local independent restaurants (cafes, family bistros, pizzerias, fine dining, and cloud kitchens).

### Why BistroPulse Exists
1. **The Chain Disadvantage:** Corporate fast-food franchises possess multi-million dollar ad budgets, but rely on mass-produced commissary food reheated in plastic bags. Independent restaurants have authentic craft, fresh morning prep, and local farmers—yet struggle to articulate their **Unique Value Proposition (UVP)**.
2. **Marketing Fragmentation & Time Poverty:** Restaurant owners work 14-hour days managing kitchen inventory, line cooks, and diners. They do not have time to manually post on Instagram, manage Facebook community groups, and text VIP customers individually.

### High-Level Architecture
* **Frontend:** React 19, TypeScript, Vite, Tailwind CSS, Lucide Icons. Designed with warm culinary dark-mode aesthetics, rich interactive modules, live smartphone simulators, and toast alerts.
* **Backend:** Node.js, Express 5 REST API, persistent JSON database.
* **Domain Engines:** Algorithmic Culinary Value Positioning Engine, Meta Graph API v20+ Automation Service, WhatsApp Cloud API & 2-Way Chatbot Concierge Service.
* **Testing:** 10-suite unit & integration test runner, end-to-end HTTP verification script.

---

## Part 2: The Value Positioning Playbook

### The Anti-Chain Contrast Principle
Diners default to corporate chains because chains are familiar and predictable. To win over diners, local restaurants must position their craft against chain shortcuts:

* **Mass Chains:** Frozen bulk sauce shipped 900 miles, par-baked dough pucks, transactional ticket numbers, profits funneling to distant private equity.
* **Independent Kitchens:** Morning scratch reduction, 48-hour fermented sourdough, real oakwood flames, direct farm partnerships, personal hospitality.

### The BistroPulse UVP Formula
$$\text{UVP} = \text{Place Anchor} + \text{Sensory Culinary Craft} + \text{The Anti-Shortcut Guarantee}$$

*Example:*  
*"Where Oakville experiences real culinary soul: zero shortcuts, daily hand-rolled pasta & 48-hour fermented sourdough crusts, and genuine hospitality you simply cannot mass-produce."*

### The 3 Core Pillars of Local Restaurant Value
1. **Uncompromising Craft:** Behind-the-scenes hand kneading, open flames, slow simmering.
2. **Hyper-Local Provenance:** Micro-farm partnerships within 35 miles.
3. **The Lost Art of Real Hospitality:** Guests treated like family, unhurried meals.

### Sensory Appetite Vocabulary vs Forbidden Commodity Words
* **Use:** *velvety*, *oakwood flame*, *simmered for 6 hours*, *hand-pinched*, *imported San Marzano*, *melt-in-your-mouth*.
* **Avoid:** *cheap food*, *fast turnover*, *discount meals*, *microwaved*.

---

## Part 3: WhatsApp Marketing & Concierge Automation

WhatsApp boasts an open rate of **94% to 98%**, making it the highest-converting communication channel for restaurants.

### 1. VIP Customer Broadcast Engine
Allows restaurants to send broadcast invitations to specific diner segments (*VIP Regulars*, *Lunch Regulars*, *Date Night*, *Inactive 30+ Days*) with dynamic personalization tags:
`Ciao {{name}}! Chef just pulled fresh Truffle Gnocchi from the oven. As our VIP, enjoy a complimentary Chianti tonight!`

### 2. Automated Post-Dining Review & Loyalty Booster
Automatically triggers a friendly WhatsApp message 2 hours after a guest pays their bill:
1. Warm thank-you from the founders and chef.
2. Direct 1-tap link to leave a 5-star Google Maps review.
3. Complimentary dessert coupon code for their next visit.

### 3. Interactive 2-Way Smartphone Chatbot Simulator
A live interactive smartphone screen inside the BistroPulse dashboard. Diners can type keywords (`MENU`, `BOOK`, `SPECIAL`, `HOURS`) or ask freeform questions and receive instant automated replies.

---

## Part 4: Instagram & Facebook Marketing Automation

### 1. AI Culinary Post & Reel Creator
Generates appetizing captions with local hashtags tailored to specific culinary storytelling angles:
* *Behind-the-Scenes Prep at 7 AM*
* *Signature Sizzle Pull*
* *Farm-to-Table Provenance*
* *Intimate Date Night*

### 2. Multi-Mode Smartphone Previewer
Toggle between:
* **Instagram Feed Post:** Square photo, username badge, like counts, and caption expander.
* **Instagram Reel:** Vertical 9:16 layout with audio credit and CTA sticker.
* **Facebook Community Card:** Post header, public badge, and *"Book Now"* / *"Send WhatsApp"* action buttons.

### 3. Comment-to-DM Auto-Responder (Viral Growth Loop)
When a user comments `MENU` or `BOOK` on an Instagram post, Meta automatically triggers a private DM to that user with the secret menu and reservation link.

### 4. Hyper-Local Meta Ad Studio
Generates targeted ad copy variations designed for a 3-to-5 mile radius ring around the restaurant address.

---

## Part 5: Omnichannel Campaign Studio & Calendar

### 1-Click Omnichannel Campaign Generator
Select a proven restaurant theme:
* *Weekend Artisanal Chef Feature*
* *Rainy Day Hearth & Comfort Drop*
* *Secret Off-Menu VIP Night*
* *Sunday Neighborhood Family Feast*

BistroPulse simultaneously drafts coordinated copy across WhatsApp, Instagram, and Facebook in one single click, with side-by-side editing and instant 1-click campaign launch.

### Content Marketing Calendar
A unified schedule of all published and scheduled marketing drops across all three channels with channel and status filtering.

---

## Part 6: VIP Diners CRM & Loyalty System

* **Diner Profiles:** Tracks guest names, phone numbers, visit frequency, last visit date, favorite signature dish, and lifetime spend.
* **Audience Segmentation:** Filter by VIPs, Lunch Regulars, Date Night regulars, or Inactive guests.
* **Direct 1-on-1 WhatsApp Invitations:** One-click personalized WhatsApp message composer that automatically inserts the diner's favorite dish.

---

## Part 7: Complete REST API Reference

All endpoints are hosted at `http://localhost:5000/api` with JSON payloads:

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/restaurant` | Retrieve active restaurant profile and differentiators |
| `PUT` | `/api/restaurant` | Update restaurant profile details |
| `GET` | `/api/positioning` | Retrieve Value Positioning Matrix (UVP, Manifesto, Pillars) |
| `POST` | `/api/positioning/generate` | AI analyzes cuisine and generates custom positioning |
| `GET` | `/api/positioning/audit` | Computes Value Health Score (0-100%), grade, and strengths |
| `PUT` | `/api/positioning` | Save manual edits to positioning matrix |
| `POST` | `/api/whatsapp/broadcast` | Dispatch broadcast to segment (`{ segment, customMessage }`) |
| `POST` | `/api/whatsapp/chat-simulator` | Test chatbot keyword reply (`{ from, text, senderName }`) |
| `POST` | `/api/whatsapp/review-booster` | Dispatch 2-hour post-dining review request with coupon |
| `POST` | `/api/meta/instagram/publish` | Publish or simulate Instagram post |
| `POST` | `/api/meta/facebook/publish` | Publish or simulate Facebook Page post |
| `POST` | `/api/meta/instagram/comment-trigger` | Test Comment-to-DM auto-responder |
| `GET` | `/api/meta/ads/local-radius` | Generate 3-to-5 mile radius Meta ad copy |
| `GET` | `/api/campaigns` | List all active and scheduled campaigns |
| `POST` | `/api/campaigns/generate` | Generate 3-channel synchronized campaign copy |
| `POST` | `/api/campaigns` | Save a new campaign |
| `GET` | `/api/calendar` | List all content calendar items |
| `POST` | `/api/calendar` | Schedule a new post |
| `DELETE` | `/api/calendar/:id` | Remove a calendar item |
| `GET` | `/api/customers` | List all CRM customer records |
| `POST` | `/api/customers` | Register a new customer |
| `GET` | `/api/analytics` | Dashboard reach, bookings, open rates, and revenue |
| `GET` | `/api/logs` | Live activity log stream |
| `POST` | `/api/settings/reset` | Reset all data to default sample trattoria |

---

## Part 8: Meta Graph API & WhatsApp Cloud API Setup Guide

BistroPulse comes with an **Interactive Simulation Mode** enabled by default. To connect live accounts:

1. **Meta for Developers:**
   - Go to [developers.facebook.com](https://developers.facebook.com) > Create App > Type: **Business**.
   - Add **WhatsApp** > View API Setup > Copy **Phone Number ID** and **WABA ID**.
   - Under Business Settings > System Users, generate a permanent token with `whatsapp_business_messaging`, `pages_manage_posts`, `instagram_basic`, and `instagram_content_publish`.
2. **Link Instagram to Facebook Page:**
   - In Facebook Page Settings > Linked Accounts, connect your Instagram Business Account.
3. **Configure in BistroPulse:**
   - Open **Settings & APIs** tab in BistroPulse.
   - Uncheck **Simulation Mode**.
   - Paste Facebook Page ID, Instagram Business Account ID, Meta Access Token, Phone Number ID, and WhatsApp Bearer Token.
   - Click **Save Configuration**.

---

## Part 9: Quick Start, Installation & Deployment

### Run Locally
```bash
# Navigate to project directory
cd C:\Users\Malaika\.gemini\antigravity\scratch\bistropulse

# Start the full-stack server
npm start
```
Open **`http://localhost:5000`** in your browser.

### Run Automated Tests
```bash
npm test
```
Executes the 10-suite unit and integration test suite.

### Run End-to-End Verification Check
```bash
node server/e2e-check.js
```
Validates all HTTP API endpoints and verifies static SPA asset delivery with HTTP 200.

---

<p align="center">
  <strong>BistroPulse — Empowering independent restaurants to thrive.</strong>
</p>
