<div align="center">
  <img src="https://ij08jc4ubp6szflu.public.blob.vercel-storage.com/sms_apk_version/icon.png" alt="Paulina SMS Gateway" width="120" />

  # Paulina SMS Gateway 🚀
  **Turn any Android Phone into an Automated, API-Driven SMS Courier.**

  [![Android Release](https://img.shields.io/badge/APK%20Release-v1.1.0-blue?logo=android)](https://ij08jc4ubp6szflu.public.blob.vercel-storage.com/sms_apk_version/smsgetway_1.1.0.apk)  
  [![Made with Node.js](https://img.shields.io/badge/Backend-Node.js-green)](https://nodejs.org/)
  [![Issues](https://img.shields.io/github/issues/DelcioLuis/paulina-sms-public)](https://github.com/DelcioLuis/paulina-sms-public/issues)
  [![License](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)
</div>

<br/>

Paulina SMS Gateway is a professional, open-source infrastructure that allows developers to seamlessly route SMS messages globally directly from their servers to any Android device using our robust Backend API and Mobile Client.

Forget about expensive carrier contracts. Plug your own SIM Cards and deliver messages through your own Android phones using our highly scalable architecture.

## ✨ Core Features
- **Plug & Play**: Connect an unlimited network of Android phones by simply scanning a QR code.
- **RESTful API**: Send SMS programmatically with any language using our developer-friendly APIs.
- **Webhooks & Telemetry**: Receive real-time Delivery Receipts (Delivered, Sent, Failed) directly to your servers or Native Integrations.
- **Native Slack & Email Digests**: Push real-time network statuses to Slack channels and daily digest reports to email.
- **End-to-End Encryption**: Assured data confidentiality out-of-the-box using the industry-standard HMAC SHA256 Webhook Signatures.

---

## 📦 1. Download & Installation

The official mobile client is continually published and strictly maintained. 

**[➡️ Download the Latest APK Here (v1.1.0)](https://ij08jc4ubp6szflu.public.blob.vercel-storage.com/sms_apk_version/smsgetway_1.1.0.apk)**

#### 🗄️ Versions Archive
| Version | Release Date | Download Link | Notes |
|---------|-------------|---------------|-------|
| `v1.1.0` | April 2026 | [📥 Get APK](https://ij08jc4ubp6szflu.public.blob.vercel-storage.com/sms_apk_version/smsgetway_1.1.0.apk) | Initial Stable Release with Slack & Email integrations. |

1. Transfer the `.apk` to your target Android Device.
2. Install the app (You might need to allow "Install from Unknown Sources" depending on your Android version).
3. Grant the required permissions `SMS` and `Background Execution` to allow background message processing.
4. Scan your Web Console **Project QR Code** to securely link the device to your data-stream.

---

## 💻 2. Integration Guide (API)

Routing an SMS is as simple as triggering a `POST` request to our master servers. See the standard implementation below.

### Sending an SMS (Node.js Example)

```javascript
fetch('http://sms-api.paulinasource.com/sms/send', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer YOUR_PROJECT_API_KEY'
    },
    body: JSON.stringify({
        projectId: "YOUR_PROJECT_ID",
        to: "+351912345678",
        message: "Your OTP is 123456. Do not share this code.",
        secret: true // Hide content from physical device outboxes
    })
})
```

---

## 🪝 3. Handling Webhooks (Delivery Reports)

Whenever your phone officially delivers a message or fails, our servers fire an event to your `Webhook URL` automatically.

**Express.js Recipient Example:**
```javascript
app.post('/webhook/sms', (req, res) => {
    const { id, to, status } = req.body;
    
    if (status === 'DELIVERED') {
        console.log(`Successfully verified receipt to ${to}`);
    } else if (status === 'FAILED') {
        console.log(`Failed to reach ${to}. Alerting operations.`);
    }

    res.sendStatus(200);
});
```

---

## 🐛 4. Bugs, Issues & Feature Requests

We heavily rely on developer feedback to keep the ecosystem stable!
If you encountered a crash, unresponsive deliveries, or want to suggest new features (like WhatsApp protocol syncing):

1. **Check Existing Issues**: Ensure your bug hasn't been [reported already](https://github.com/DelcioLuis/paulina-sms-public/issues).
2. **Open a New Issue**: Please include the **Device Model**, **Android Version**, and any relevant **cURL logs** so we can trace the misfire.

[🐞 Click here to Report a Bug / Open Issue](https://github.com/DelcioLuis/paulina-sms-public/issues/new)

---

## 🛡️ Telemetry & Reliability Notes
- We highly recommend ensuring your Android device disables "Battery Optimization" for the `Paulina` app. Strict OS battery killers (like MIUI or EMUI) might force the app to sleep, creating unnatural backlogs of un-sent messages.
- The default limit is evaluated to Android's built-in maximum (about 30 SMS per 30 minutes dynamically). If you need ultra-high capacity, connect multiple Android endpoints.

<div align="center">
  <sub>Built with ❤️ for modern Fintech and Software Ecosystems.</sub>
</div>
