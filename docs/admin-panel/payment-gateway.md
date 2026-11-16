---
sidebar_position: 12
---

# Payment Gateway

Payment gateways are turned on and configured in the admin panel under **Settings → Payment Methods** (card in the **Selling** group of the Settings hub, route `/payment_methods`, permission `manage_payment_methods`). The gateways you turn on here are the payment options customers see at checkout in the customer app and on the website.

eMarket supports these 10 payment methods:

- Cash on Delivery
- PayPal
- Razorpay
- Paystack
- Stripe
- Midtrans
- PhonePe
- Cashfree
- PayTabs
- DPO Pay

![Payment Methods](/img/detailed-documentation/payment-methods.webp)

## How the Payment Methods screen works

- **Gateway list (left)**: shows how many methods are turned on (e.g. "1 / 10 payment methods turned on"), **All / On / Off** tabs and a **Search gateways…** box. A green dot means on, grey means off, amber means on but **Needs setup**. Gateways with a mode show a **Live** or **Test** badge.
- **Enabled / Disabled** switch: turns the selected gateway on or off. You can fill in the details while it is off and turn it on later.
- **Payment Mode**: **Sandbox** ("Test payments, no real money") or **Live** ("Real payments from customers"). Shown for every gateway except Cash on Delivery, Razorpay and Paystack.
- **Credentials**: the gateway's keys. Secret keys have an eye button to show or hide them. Currency fields have a "supported … Learn more" link to the gateway's list of currencies.
- **Webhook & callback URLs**: URLs with a **Copy** button. Paste them into the gateway's dashboard so it can tell your store when a payment succeeds.
- **Save bar** at the bottom: "Unsaved changes" or "All changes saved", with **Discard** and **Update**. **Update** saves all gateways at once; **Discard** undoes every unsaved change on the page.

:::caution
- At least one payment method must stay on. Saving with all of them off is refused ("Turn on at least one payment method.").
- If an enabled gateway is missing a required field, **Update** opens that gateway and lists the missing fields instead of saving.
- Switch each gateway from **Sandbox** to **Live** and paste your live keys before you launch, or payments stay test payments.
:::

## Fields per gateway

`your-domain` is the address of your admin panel. The URLs are filled in automatically; copy them from the screen.

| Gateway | Mode | Credentials (as labelled on screen) | Webhook & callback URLs |
| :--- | :--- | :--- | :--- |
| **Cash on Delivery** | — | **COD Mode**: Global (COD for every product) or Product wise (only products that allow COD). | — |
| **PayPal** | Sandbox / Live | Paypal Business Email\*, Currency Code\* | Notification URL (IPN): `https://your-domain/customer/ipn` |
| **Razorpay** | — | Razorpay key ID, Secret Key | — |
| **Paystack** | — | Paystack Public Key\* (shown as "Paystack Pubic Key"), Paystack Secret Key\*, Currency Code\* | — |
| **Stripe** | Sandbox / Live | Stripe Publishable Key, Stripe Secret Key, Stripe Webhook Secret Key, Currency Code\* | Payment Endpoint URL: `https://your-domain/webhook/stripe` |
| **Midtrans** | Sandbox / Live | Server Key | Notification URL: `https://your-domain/midtrans/callback`; Return URL: your website's `/web-payment-status` page |
| **PhonePe** | Sandbox / Live | Merchant ID, Client ID, Client Version, Client Secret | Payment Endpoint URL: `https://your-domain/phonepe/callback` (editable) |
| **Cashfree** | Sandbox / Live | App ID, Secret Key | Notification URL: `https://your-domain/cashfree/callback` |
| **PayTabs** | Sandbox / Live | Profile ID, Secret Key | Notification URL: `https://your-domain/paytabs/callback` |
| **DPO Pay** | Sandbox / Live | Company Token, Service Type (e.g. `3854`), Currency Code\* | Notification URL: `https://your-domain/dpo/callback` |

\* Required while the gateway is on. The **Payment Mode** is also required for gateways that have one.

The currency of PayPal, Stripe, Paystack and DPO Pay is set on the gateway itself; the store currency in Store Settings → **Currency Setting** is only used for showing prices. See [Payment Methods](../detailed-documentation/settings.mdx#3-payment-methods-payment_methods) in the detailed documentation for more examples.

Follow the steps below to get the credentials from each gateway's dashboard.

## Stripe

1. Go to [https://dashboard.stripe.com/login](https://dashboard.stripe.com/login) and sign in with your Stripe account.
   ![Stripe 1](/img/admin-panel/stripe1.webp)
2. Click **Developers** at the top right.
   ![Stripe 2](/img/admin-panel/stripe2.webp)
3. Click **API keys** in the left navigation.
   ![Stripe 3](/img/admin-panel/stripe3.webp)
4. Click **Reveal key** and copy the **Publishable key** and **Secret key**. Use the test keys for Sandbox and the live keys for Live.
   ![Stripe 4](/img/admin-panel/stripe4.webp)
5. In Stripe, under **Developers → Webhooks**, add an endpoint with the **Payment Endpoint URL** copied from the panel, then copy its **Signing secret** (`whsec_…`).
6. In the panel open **Settings → Payment Methods → Stripe**, turn it **Enabled**, pick **Sandbox** or **Live**, paste the **Stripe Publishable Key**, **Stripe Secret Key** and **Stripe Webhook Secret Key**, choose the **Currency Code** and click **Update**.
   ![Stripe](/img/admin-panel/stripe.webp)

## Razorpay

1. Go to [https://dashboard.razorpay.com/](https://dashboard.razorpay.com/) and sign in with your Razorpay account.
   ![RP](/img/admin-panel/rp.webp)
2. Click **Settings**.
   ![RP 1](/img/admin-panel/rp1.webp)
3. Click **API Keys**.
   ![RP 2](/img/admin-panel/rp2.webp)
4. Generate a new key (or regenerate it) and copy the **Key ID** and **Key Secret**.
   ![RP 3](/img/admin-panel/rp3.webp)
5. In the panel open **Settings → Payment Methods → Razorpay**, turn it **Enabled**, paste the **Razorpay key ID** and **Secret Key** and click **Update**. Razorpay has no Payment Mode on this screen: test or live depends on the key pair you paste.
   ![Razorpay](/img/admin-panel/razorpay.webp)

## Paystack

1. Go to [https://dashboard.paystack.com/](https://dashboard.paystack.com/) and sign in with your Paystack account.
   ![PS](/img/admin-panel/ps.webp)
2. Click **Settings**, then **API Keys & Webhooks**.
   ![PS 1](/img/admin-panel/ps1.webp)
3. Copy the **Public Key** and **Secret Key** (test keys for testing, live keys for real payments).
   ![PS 2](/img/admin-panel/ps2.webp)
4. In the panel open **Settings → Payment Methods → Paystack**, turn it **Enabled**, paste both keys, choose the **Currency Code** and click **Update**.
   ![Paystack](/img/admin-panel/paystack.webp)

## PayPal

1. Sign in to your PayPal **business** account (for testing, use a sandbox business account from [developer.paypal.com](https://developer.paypal.com/)).
2. In the panel open **Settings → Payment Methods → PayPal**, turn it **Enabled** and pick **Sandbox** or **Live**.
3. Enter your **Paypal Business Email** and choose the **Currency Code** (it must be a currency PayPal supports).
4. Copy the **Notification URL (IPN)** and enter it as the IPN URL in your PayPal account settings.
5. Click **Update**.

## Midtrans, PhonePe, Cashfree and PayTabs

1. Sign in to the gateway's merchant dashboard and open its API keys / developer section (use the sandbox or test environment first).
2. Copy the credentials the panel asks for:
   - **Midtrans**: Server Key.
   - **PhonePe**: Merchant ID, Client ID, Client Version and Client Secret.
   - **Cashfree**: App ID and Secret Key.
   - **PayTabs**: Profile ID and Secret Key (server key).
3. In the panel open **Settings → Payment Methods**, select the gateway, turn it **Enabled**, pick **Sandbox** or **Live** to match the keys, and paste the credentials.
4. Copy the URLs under **Webhook & callback URLs** into the gateway dashboard's notification / webhook settings.
5. Click **Update**.

## DPO Pay

1. Go to the DPO Pay portal ([https://dpogroup.com/](https://dpogroup.com/)) and sign in with your DPO Pay merchant account.
2. Open your merchant dashboard and go to **Settings** or **Integration Settings**.
3. Copy your **Company Token** and **Service Type**.
4. In the panel open **Settings → Payment Methods → DPO Pay**, turn it **Enabled** and pick **Sandbox** or **Live**.
5. Paste the **Company Token** and **Service Type**, choose the **Currency Code**, copy the **Notification URL** into DPO if asked, and click **Update**.
   ![DPO Pay](/img/admin-panel/payment-methods-dpo.webp)
