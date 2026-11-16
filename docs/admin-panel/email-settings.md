---
sidebar_position: 8
---

# Email Settings

Set up the mail server that eMarket uses to send emails (order emails, emails you send from the panel, test emails). Click **Settings** in the sidebar, then the **SMTP Mail Setting** card (group **Communication**). It opens Store Settings on the **SMTP Mail Setting** pill (`/store_settings?section=smtp_mail_setting`).

![SMTP Mail Setting](/img/admin-panel/email_settings.webp)

## Mail Server

- **Mailer**: the mail driver, **SMTP** or **Sendmail**.
- **From Email ID**: the address emails are sent from. It is also the SMTP user name.
- **Reply To Email ID**: the address customers reply to.
- **SMTP Email Password**: the password (or app password) of the From account.
- **SMTP Host**: for example `smtp.gmail.com`.
- **SMTP Port**: TLS: 587, SSL: 465.
- **SMTP Email Content Type**: **HTML** or **Text**.
- **SMTP Encryption**: **TLS** or **SSL**. It must match the port.

## Email Test

Enter an address in **Email Test** and click **Test Mail**. The test uses the values currently in the form, so you can check them before you click **Update**.

## Configuration Steps

1. Click **Settings** in the sidebar, then the **SMTP Mail Setting** card.
2. Choose **Mailer** `SMTP`.
3. Enter **From Email ID**, **Reply To Email ID** and **SMTP Email Password**.
4. Enter **SMTP Host**, **SMTP Port** and **SMTP Encryption** (for example `smtp.gmail.com`, `587`, `TLS`).
5. Choose **SMTP Email Content Type** `HTML`.
6. Enter your own address in **Email Test** and click **Test Mail**. Check your inbox.
7. Click **Update**.

## Which Emails Are Sent

- **Order status emails**: choose which order statuses send an email in the profile menu (top right) → **Settings** → **Order Mail Settings**. See [Account Settings](../detailed-documentation/settings.mdx#13-account-settings-order-mail-settings-settings).
- **Emails you send yourself**: sidebar **Email → Manage Emails** and **Email → Email Templates**. See [Send Email](../detailed-documentation/communications.mdx#5-send-email-emails) and [Email Templates](../detailed-documentation/communications.mdx#4-email-templates-email_templates).

## Important Notes

- Use a dedicated mailbox for sending, and keep its password safe.
- For Gmail, turn on 2-step verification and use an app password in **SMTP Email Password**.
- Without a From address and host, emails are skipped and a warning is written to the log.
- The **System Status** card on the Settings hub shows whether mail is configured.

## Troubleshooting

1. **Emails not sending**: run **Test Mail** and read the error. Check host, port and encryption (587 with TLS, 465 with SSL) and that your server allows outgoing connections on that port.
2. **Emails going to spam**: send from an address on your own domain and set up SPF, DKIM and DMARC records for it.

## Support

For assistance with email configuration, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
