# 🔌 BistroPulse REST API Documentation

This document provides a comprehensive technical reference for all REST API endpoints provided by the BistroPulse backend server.

Base URL: `http://localhost:5000/api`  
Content-Type: `application/json`

---

## 📋 Table of Contents
1. [Restaurant Profile API](#1-restaurant-profile-api)
2. [Value Positioning Engine API](#2-value-positioning-engine-api)
3. [WhatsApp Automation API](#3-whatsapp-automation-api)
4. [Meta (Instagram & Facebook) Automation API](#4-meta-instagram--facebook-automation-api)
5. [Omnichannel Campaigns API](#5-omnichannel-campaigns-api)
6. [Content Marketing Calendar API](#6-content-marketing-calendar-api)
7. [VIP Diners CRM API](#7-vip-diners-crm-api)
8. [Analytics & Activity Logs API](#8-analytics--activity-logs-api)
9. [Settings & Configuration API](#9-settings--configuration-api)

---

## 1. Restaurant Profile API

### `GET /api/restaurant`
Retrieves the active restaurant's profile, signature dishes, differentiators, and target diner segments.

#### Example Request:
```bash
curl -X GET http://localhost:5000/api/restaurant
```

#### Example Response (200 OK):
```json
{
  "id": "resto-1",
  "name": "The Rustic Olive Trattoria",
  "tagline": "Wood-Fired Soul, Hand-Rolled Heritage",
  "cuisine": "Artisanal Italian & Wood-Fired Trattoria",
  "address": "442 Elm Street, Downtown Arts District",
  "city": "Oakville",
  "phone": "+1 (555) 234-8901",
  "whatsappNumber": "+1 (555) 234-8901",
  "instagramHandle": "@rusticolivetrattoria",
  "facebookPage": "Rustic Olive Trattoria Oakville",
  "priceTier": "$$ (Affordable Craft Dining)",
  "signatureDishes": [
    {
      "name": "48h Fermented Truffle Burrata Pizza",
      "price": "$22",
      "usp": "Oakwood-fired crust with fresh Puglia burrata & shaved summer truffle"
    }
  ],
  "differentiators": [
    "100% Zero Microwave Kitchen: Everything prepared fresh over open oakwood",
    "Local Farm-to-Table: Partnered with 4 local farms within 35 miles"
  ]
}
```

---

### `PUT /api/restaurant`
Updates the restaurant profile details.

#### Example Request:
```bash
curl -X PUT http://localhost:5000/api/restaurant \
  -H "Content-Type: application/json" \
  -d '{
    "name": "The Rustic Olive Trattoria",
    "tagline": "Real Wood Smoke, Zero Corporate Shortcuts",
    "city": "Oakville"
  }'
```

---

## 2. Value Positioning Engine API

### `GET /api/positioning`
Retrieves the restaurant's active Value Positioning Matrix including the Unique Value Proposition (UVP), Anti-Chain Manifesto, Value Pillars, Brand Voice, and Social Hooks.

#### Example Request:
```bash
curl -X GET http://localhost:5000/api/positioning
```

#### Example Response (200 OK):
```json
{
  "archetype": "The Passionate Culinary Artisan & Community Anchor",
  "coreUsp": "Where Oakville experiences real culinary soul: zero shortcuts, daily hand-rolled pasta & 48-hour fermented sourdough crusts, and genuine hospitality you simply cannot mass-produce.",
  "antiChainManifesto": "Big restaurant chains ship frozen pre-made sauce in plastic bags from distribution centers 900 miles away. Chef Marco lights our oakwood fire at 6:00 AM...",
  "brandVoice": {
    "tone": "Warm, Proud, Hospitable, Sensual & Flavor-Focused",
    "keywords": ["Handcrafted", "Oak-Fired", "Simmered with Love"],
    "prohibitedPhrases": ["Cheap eats", "Fast turnaround", "Processed"]
  },
  "valuePillars": [
    {
      "pillar": "Uncompromising Craftsmanship",
      "description": "Every strand of tagliatelle and every pizza dough undergoes artisanal fermentation.",
      "marketingAngle": "Behind-the-scenes flour dusting, chef hands shaping dough."
    }
  ]
}
```

---

### `POST /api/positioning/generate`
Triggers the AI Positioning Engine to analyze the restaurant's current cuisine style and generate an authentic positioning matrix tailored to that cuisine.

#### Example Request:
```bash
curl -X POST http://localhost:5000/api/positioning/generate
```

---

### `GET /api/positioning/audit`
Audits the restaurant's value differentiation strength and returns a **0-100% score**, grade, strengths list, and actionable recommendations.

#### Example Request:
```bash
curl -X GET http://localhost:5000/api/positioning/audit
```

#### Example Response (200 OK):
```json
{
  "score": 100,
  "grade": "A+ (Culinary Destination)",
  "strengths": [
    "Compelling founder heritage & emotional origin story",
    "Strong list of concrete, verifiable culinary differentiators",
    "Vivid anti-chain contrast statement that exposes mass-market food shortcuts"
  ],
  "recommendations": []
}
```

---

## 3. WhatsApp Automation API

### `POST /api/whatsapp/broadcast`
Dispatches a personalized broadcast message to a customer segment.

#### Request Body:
```json
{
  "segment": "VIP Regular",
  "customMessage": "Ciao {{name}}! 🍷 Chef Marco prepared an off-menu autumn feature tonight. Reply BOOK to hold a table!"
}
```

#### Example Response (200 OK):
```json
{
  "segment": "VIP Regular",
  "recipientCount": 14,
  "deliveredCount": 14,
  "estimatedOpenRate": "96%",
  "messages": [
    {
      "success": true,
      "mode": "simulation",
      "to": "+15554921029",
      "customerName": "Sofia Martinez",
      "readStatus": "read"
    }
  ]
}
```

---

### `POST /api/whatsapp/chat-simulator`
Simulates an incoming WhatsApp message to the restaurant's 2-way concierge chatbot.

#### Request Body:
```json
{
  "from": "+15553819921",
  "text": "What are your SPECIALS tonight?",
  "senderName": "David"
}
```

#### Example Response (200 OK):
```json
{
  "incoming": {
    "from": "+15553819921",
    "text": "What are your SPECIALS tonight?",
    "senderName": "David",
    "timestamp": "2026-10-16T10:00:00.000Z"
  },
  "outgoing": {
    "to": "+15553819921",
    "reply": "🌟 *Chef Marco’s Autumn Truffle Feature*\nFresh black autumn truffles shaved table-side over hand-rolled ricotta gnocchi ($26). Limited to 20 servings daily!",
    "timestamp": "2026-10-16T10:00:00.500Z"
  }
}
```

---

### `POST /api/whatsapp/review-booster`
Triggers the automated post-dining review request flow with a complimentary dessert / coupon incentive.

#### Request Body:
```json
{
  "customerId": "cust-1"
}
```

#### Example Response (200 OK):
```json
{
  "customer": { "name": "Sofia Martinez", "phone": "+15554921029" },
  "message": "Ciao Sofia! Thank you for dining with us tonight... Show this reply on your next visit for a complimentary dessert!",
  "status": "sent",
  "incentiveProvided": "Complimentary House Tiramisu"
}
```

---

## 4. Meta (Instagram & Facebook) Automation API

### `POST /api/meta/instagram/publish`
Publishes or simulates a post to the restaurant's Instagram Business Account.

#### Request Body:
```json
{
  "caption": "Sound on 🔊 That sizzle when 900°F oak flame meets 48-hour fermented crust! #OakvilleEats",
  "imageUrl": "https://images.unsplash.com/photo-1513104890138-7c749659a591",
  "mediaType": "IMAGE"
}
```

#### Example Response (200 OK):
```json
{
  "success": true,
  "mode": "simulation",
  "postId": "ig_981a2f4c",
  "estimatedReach": 2840,
  "publishedAt": "2026-10-16T11:00:00.000Z"
}
```

---

### `POST /api/meta/instagram/comment-trigger`
Simulates a follower commenting on an Instagram post, triggering the Comment-to-DM growth engine.

#### Request Body:
```json
{
  "username": "foodie_dan",
  "commentText": "Please send MENU link!",
  "postTitle": "Fresh Autumn Truffles"
}
```

#### Example Response (200 OK):
```json
{
  "matched": true,
  "triggerKeyword": "MENU",
  "user": "foodie_dan",
  "comment": "Please send MENU link!",
  "sentDm": "Ciao! 🍝 Here is our secret off-menu specials & live booking link: https://rusticolivetrattoria.local/specials?ref=ig_dm",
  "timestamp": "2026-10-16T11:05:00.000Z"
}
```

---

### `GET /api/meta/ads/local-radius`
Generates hyper-local Meta ad copy targeting a 3-to-5 mile radius around the restaurant's address.

#### Example Response (200 OK):
```json
{
  "campaignObjective": "Local Store Visits & Table Bookings",
  "recommendedBudget": "$5 - $10 / day",
  "geographicTargeting": {
    "radius": "3 to 5 miles around 442 Elm Street",
    "city": "Oakville",
    "demographics": "Ages 24–65, Interests: Local Dining, Farm-to-Table, Date Night"
  },
  "adVariations": [
    {
      "angle": "Anti-Chain Freshness",
      "headline": "Still Eating Frozen Chain Food? Taste Real Oakville Craft",
      "primaryText": "At The Rustic Olive Trattoria, we don't do pre-packaged bags...",
      "callToAction": "Book Table / Send WhatsApp"
    }
  ]
}
```

---

## 5. Omnichannel Campaigns API

### `POST /api/campaigns/generate`
Generates synchronized messaging across WhatsApp, Instagram, and Facebook for a selected theme.

#### Request Body:
```json
{
  "theme": "weekend_special",
  "targetSegment": "VIP Regulars"
}
```

#### Example Response (200 OK):
```json
{
  "title": "Artisanal Weekend Chef Feature",
  "theme": "Culinary Craftsmanship & Scarcity",
  "channels": ["whatsapp", "instagram", "facebook"],
  "content": {
    "whatsapp": "Hey {{name}}! 🍽️ Chef at The Rustic Olive Trattoria prepared a special off-menu tasting...",
    "instagram": "Sound up 🔊 Fresh aromas filling the dining room! Chef is putting finishing touches...",
    "facebook": "Oakville community: This weekend, escape the busy week with an authentic meal..."
  },
  "scheduleSuggestion": {
    "whatsappBestTime": "Friday 4:30 PM",
    "instagramBestTime": "Friday 11:45 AM",
    "facebookBestTime": "Thursday 6:30 PM"
  }
}
```

---

## 6. Content Marketing Calendar API

* `GET /api/calendar` — Returns all scheduled and published items.
* `POST /api/calendar` — Add a new item (`{ date, time, channel, type, title, caption, status }`).
* `PUT /api/calendar/:id` — Update an existing calendar item.
* `DELETE /api/calendar/:id` — Remove an item from the calendar.

---

## 7. VIP Diners CRM API

* `GET /api/customers` — Returns all registered diners with visit counts, favorite dishes, and lifetime spend.
* `POST /api/customers` — Register a new customer (`{ name, phone, email, segment, favoriteDish, notes }`).
* `PUT /api/customers/:id` — Update customer information.

---

## 8. Analytics & Activity Logs API

### `GET /api/analytics`
Returns key marketing performance indicators:
```json
{
  "monthlyEstimatedReach": 14200,
  "tableBookingsInitiated": 67,
  "whatsappOpenRate": "94.2%",
  "instagramEngagementRate": "7.8%",
  "estimatedRevenueDriven": "$5,695",
  "recentChannelPerformance": [
    { "channel": "WhatsApp VIP Broadcasts", "bookings": 29, "openRate": "96%", "roiMultiplier": "14.2x" },
    { "channel": "Instagram Reels & Stories", "bookings": 22, "roiMultiplier": "8.4x" },
    { "channel": "Facebook Hyper-Local Ads", "bookings": 16, "roiMultiplier": "6.1x" }
  ]
}
```

### `GET /api/logs`
Returns the recent stream of all automated dispatches, chatbot conversations, and published posts.

---

## 9. Settings & Configuration API

* `GET /api/settings` — Returns current API keys, phone number IDs, and simulation mode status.
* `PUT /api/settings` — Updates Meta and WhatsApp credentials.
* `POST /api/settings/reset` — Resets all store data back to the default sample trattoria.
