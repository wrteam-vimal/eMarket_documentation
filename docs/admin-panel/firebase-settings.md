---
sidebar_position: 10
---

# Firebase Settings

Firebase is used to send push notifications (to customers, sellers, delivery boys and logged-in admin browsers) and for Firebase phone login. The keys are entered in the admin panel under **Settings → Firebase Settings** (card in the **Communication** group of the Settings hub, route `/firebase-settings`, permission `manage_Notification_settings`). For the app side of the setup, see the Flutter app documentation.

![Firebase Settings](/img/detailed-documentation/firebase-settings.webp)

## Fields

The page has one card, **Firebase Setup & Keys**, with two parts.

**Firebase Setup & Keys Form** (all required):

| Field | What to enter | Example |
| :--- | :--- | :--- |
| apiKey | Web API key of the Firebase project. | `AIzaSy…` |
| authDomain | Auth domain. | `your-project.firebaseapp.com` |
| projectId | Project ID. | `your-project` |
| storageBucket | Storage bucket. | `your-project.appspot.com` |
| messagingSenderId | Sender ID for Cloud Messaging. | `104857600123` |
| appId | Web app ID. | `1:104857600123:web:…` |
| measurementId | Analytics measurement ID. | `G-XXXXXXXXXX` |

**Firebase Json file upload**: the service-account file of the project (**Supported formats: JSON**). Once a file is saved, the label shows **File exists**. Leave the upload box empty to keep the saved file.

## Configuration steps

1. **Create a Firebase project**
   - Go to the [Firebase Console](https://console.firebase.google.com/) and create a project (or open the one your apps use).
   - Under **Project settings → General**, add a **Web app** if you have none.
2. **Copy the web config**
   - In **Project settings → General → Your apps**, open the web app and copy the values of its `firebaseConfig`.
   - In the panel open **Settings → Firebase Settings** and paste them into **apiKey**, **authDomain**, **projectId**, **storageBucket**, **messagingSenderId**, **appId** and **measurementId**.
3. **Upload the service-account file**
   - In Firebase open **Project settings → Service accounts** and click **Generate new private key**. A JSON file is downloaded.
   - Drop that file on the upload box ("Drop, paste or click to upload").
4. Click **Update**. The label now shows **File exists**.
5. **Test**: open **Settings → Notification Templates** and use **Send test to me** to check that notifications arrive.

## Phone login with Firebase

To let customers sign in with a phone number through Firebase:

1. In the Firebase Console open **Authentication → Sign-in method** and enable **Phone** (and **Google** / **Apple** if you offer those logins).
2. In the panel open **Settings → Login Setting** (Store Settings, `/store_settings?section=login_setting`) and turn on **Firebase Authentication** under *Phone authentication*. See [Login Setting](../detailed-documentation/settings.mdx#login-setting-and-the-demo-mode-toggle).

## Important notes

- The keys must belong to the **same Firebase project** as the one built into your mobile apps; otherwise notifications do not reach the apps.
- Without these settings, **Send Notification** and the template tests cannot deliver anything.
- Upload a new JSON file only when you change the service account. Keep the file private: it gives full access to your Firebase project.
- More details: [Firebase Settings](../detailed-documentation/settings.mdx#6-firebase-settings-firebase-settings) in the detailed documentation.
