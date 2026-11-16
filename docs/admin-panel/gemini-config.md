---
sidebar_position: 10
---

# Gemini API Integration Guide

eMarket uses Google **Gemini** (AI) to write product descriptions and blog content, and to fill in translations (the **Translate Empty Fields** / **Translate & Overwrite** buttons on multi-language fields). This guide shows how to generate a **Gemini API Key** and add it to the admin panel.
Reference: [Google Gemini API Docs](https://ai.google.dev/gemini-api/docs)

---

## 1. Generate Gemini API Key

### Step 1 - Go to Gemini API Docs
Open the official [Gemini API documentation](https://ai.google.dev/gemini-api/docs) and click **"Get a Gemini API Key"**.

![Get Gemini API Key](/img/flutter-partner-app/gemini1.webp)

---

### Step 2 - Create an API Key in Google AI Studio
1. In **Google AI Studio**, go to the **API Keys** section.
2. Click **"Create API Key"**.
3. Your new API key is shown in the **API key list**.
4. Copy the generated key.

![Create API Key](/img/flutter-partner-app/gemini2.webp)

---

## 2. Add Gemini API Key to the admin panel

### Step 3 - Paste the key into Third Party API Credentials
1. In the admin panel, open **Settings** and click the **Third Party API Credentials** card (group **Integrations**). It opens Store Settings on that section (`/store_settings?section=third_party_api_credentials`).
2. Paste the key into the **Gemini Key** field (group *AI content*).
3. Click **Update**. Only the Gemini key is saved by this button.

![Add Gemini API Key](/img/admin-panel/gemini-key-settings.webp)

:::note
- Third Party API Credentials now holds only the Gemini key. The Google **Place Api Key** and **Map Api Key** moved to **Address Setting → Map Provider**, see [Map API Key Settings](./map-api-key-settings.md).
- Saving needs the `manage_store_settings` permission. In demo mode the field is empty and read-only.
- If the key is missing, AI actions fail with "Google Gemini API key not configured".
:::

---

## Flow Direction Summary
1. **Generate Key** → Visit [Gemini API Docs](https://ai.google.dev/gemini-api/docs) → Click *Get a Gemini API Key*.
2. **Create Key** → In Google AI Studio → API Keys → Click *Create API Key* → Copy the key.
3. **Integrate Key** → Admin panel → **Settings → Third Party API Credentials** → paste it into **Gemini Key** → Click **Update**.
