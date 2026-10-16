# 🔑 Meta Graph API & WhatsApp Cloud API Onboarding Guide

This guide walks you through connecting your live **Facebook Page**, **Instagram Professional Account**, and **WhatsApp Business Cloud API** to BistroPulse for real-world automated dispatches.

> [!NOTE]
> BistroPulse operates in **Simulation Mode** by default. You do **not** need these credentials to test, demo, or develop the platform. Follow this guide only when you are ready to publish posts and messages to your live social accounts.

---

## 📋 Prerequisites
1. A **Facebook Personal Account** with Admin rights to your Restaurant's Facebook Page.
2. An **Instagram Professional Account** (Business or Creator) linked to your Facebook Page.
3. A phone number dedicated to WhatsApp Business (must be able to receive SMS or voice calls for verification, and not currently registered on a consumer WhatsApp app).

---

## Part 1: Setting Up WhatsApp Business Cloud API

Meta provides the **WhatsApp Cloud API** directly through Meta for Developers (no third-party BSP markup fees).

### Step 1: Create a Meta Developer App
1. Go to [developers.facebook.com](https://developers.facebook.com) and log in.
2. Click **My Apps** > **Create App**.
3. Select **Other** as the app use case > Click **Next**.
4. Select **Business** as the app type > Click **Next**.
5. Name your app (e.g. `BistroPulse Restaurant Marketing`) and link your **Meta Business Account**.
6. Click **Create App**.

### Step 2: Add WhatsApp to Your App
1. In the App Dashboard, locate **WhatsApp** and click **Set Up**.
2. Under the left sidebar, click **WhatsApp** > **API Setup**.
3. Here you will see:
   - **Temporary Access Token** (valid for 24 hours)
   - **Phone Number ID** (a 15-digit number)
   - **WhatsApp Business Account ID (WABA ID)**
4. In the *"To"* field, enter your personal mobile phone number and click **Send Message** to verify Meta's test sandbox.

### Step 3: Add Your Restaurant's Production Phone Number
1. Under **API Setup**, scroll down to **Step 5: Add a phone number**.
2. Click **Add Phone Number**.
3. Enter your restaurant's display name, category (*Food & Beverage*), and description.
4. Enter the phone number and verify it via SMS OTP.
5. Your production **Phone Number ID** will now be available.

### Step 4: Generate a Permanent System User Token
Temporary tokens expire in 24 hours. To generate a token that never expires:
1. Go to [business.facebook.com/settings](https://business.facebook.com/settings).
2. Under **Users**, click **System Users** > Click **Add**.
3. Name it `BistroPulse Admin`, set role to **Admin**.
4. Click **Add Assets** > Assign your WhatsApp Account with Full Control.
5. Click **Generate New Token**:
   - Select your BistroPulse App.
   - Check the following permissions:
     - `whatsapp_business_messaging`
     - `whatsapp_business_management`
6. Click **Generate Token** and copy the resulting string (`EAABz...`).

---

## Part 2: Setting Up Instagram & Facebook Meta Graph API

### Step 1: Link Instagram to Your Facebook Page
1. Open your Restaurant's **Facebook Page**.
2. Go to **Settings** > **Linked Accounts** > **Instagram**.
3. Click **Connect Account** and log in with your Instagram Business Account.
4. Ensure *Allow access to Instagram messages in Inbox* is enabled.

### Step 2: Find Your IDs
* **Facebook Page ID:** On your Facebook Page, click the **About** tab > scroll down to **Page Transparency** or **Page ID**.
* **Instagram Business Account ID:** 
  1. Open the [Meta Graph API Explorer](https://developers.facebook.com/tools/explorer/).
  2. Select your App and Page Token.
  3. Query `me?fields=instagram_business_account`.
  4. The returned `id` is your `instagramAccountId`.

### Step 3: Grant System User Permissions for Instagram & Facebook
In [business.facebook.com/settings](https://business.facebook.com/settings) under your System User:
1. Click **Generate New Token** (or update your token).
2. Check the following permissions:
   - `pages_show_list`
   - `pages_read_engagement`
   - `pages_manage_posts`
   - `instagram_basic`
   - `instagram_content_publish`
   - `instagram_manage_messages`
   - `instagram_manage_comments`
3. Copy the permanent access token.

---

## Part 3: Connecting to BistroPulse

1. Open BistroPulse at `http://localhost:5000`.
2. Click the **Settings & APIs** tab in the top navigation bar.
3. In the **Meta Graph API** box:
   - Uncheck **Simulation Mode**.
   - Paste your **Facebook Page ID**.
   - Paste your **Instagram Business Account ID**.
   - Paste your **Meta System User Access Token**.
   - Set your Comment-to-DM trigger keyword (e.g. `MENU` or `BOOK`).
4. In the **WhatsApp Cloud API** box:
   - Uncheck **Simulation Mode**.
   - Paste your **Phone Number ID**.
   - Paste your **WhatsApp Business Account ID (WABA ID)**.
   - Paste your **WhatsApp Cloud API Permanent Token**.
5. Click **Save Configuration**.

---

## Part 4: Webhook Configuration for 2-Way Chatbot & Comments

To receive incoming WhatsApp messages and Instagram comments in real time:

1. In the Meta Developer Dashboard, click **Webhooks**.
2. Select **WhatsApp Business Account** > Click **Subscribe to this object**.
3. Set Callback URL: `https://your-public-domain.com/api/whatsapp/webhook`
4. Set Verify Token: (a custom passphrase of your choice).
5. Subscribe to the `messages` event.
6. For Instagram: Select **Instagram** in Webhooks > Subscribe to `comments` and `messages`.

> [!TIP]
> For local testing of inbound webhooks, you can expose your local port 5000 using **ngrok**:
> ```bash
> ngrok http 5000
> ```
> Use the generated `https://xxxx.ngrok-free.app` as your Callback URL in the Meta Developer Portal.
