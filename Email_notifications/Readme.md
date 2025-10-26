# 📧 Email Notification Workflow Integration

## 📘 Overview
The **Email Notification Block** in Roboflow enables you to automatically send notifications via email using **SMTP (Simple Mail Transfer Protocol)**.  
SMTP is the protocol used for sending emails between servers — when Roboflow sends a notification, it communicates with an outgoing mail server which relays your message to the recipient.

---

## ⚙️ Key Concepts
| Parameter | Description | Example |
|------------|-------------|----------|
| **SMTP Server / Host** | The mail server used to send emails | `smtp.gmail.com`, `smtp.sendgrid.net` |
| **SMTP Port** | Network port used by the SMTP server | `23`, `587` (STARTTLS), `465` (SMTPS) |
| **Sender Email Address** | The email ID used to send notifications | `yourname@gmail.com` |
| **Receiver Email Address** | The recipient’s email ID | `user@example.com` |
| **App Password** | Special password for secure app access | Generated from Google Account |
| **Protocol** | Secure connection type | `STARTTLS` or `SMTPS` |

---

## 🔐 Generating an App Password (for Gmail)
Because Gmail and some other providers enforce **2-Step Verification**, your normal password won’t work.  
Instead, you’ll generate an **App Password** that functions like an API key for third-party access.

### Steps:
1. Visit **[Google App Passwords](https://myaccount.google.com/apppasswords)**
2. Select your account (sign in if prompted)
3. Click **Select App → Other (Custom name)**  
   Enter a name like `Roboflow_Email`
4. Click **Generate**
5. Copy the **16-character app password**
6. Use this password in your Roboflow Email Notification block

🧠 Think of this App Password as a secure “key” that allows Roboflow to send emails on your behalf.

---

## ⚙️ Configuring the Roboflow Email Block
Once you have your credentials ready, fill out the Email block as follows:

| Field | Example | Description |
|--------|----------|-------------|
| **Sender Email** | `yourname@gmail.com` | The email address sending the notification |
| **Sender Password** | `generated_app_password` | The app password from Google |
| **Receiver Email** | `recipient@example.com` | Where the message should be sent |
| **SMTP Server** | `smtp.gmail.com` | The outgoing mail server |
| **SMTP Port** | `465` | Secure SMTP (SMTPS) port |

✅ Make sure you use **port 465** for secure email transfer.

---

## 💬 Sending Message Parameters
Just like with other notification blocks, you can dynamically send values from your workflow using **Message Parameters**.

Each parameter has a **name** and **data** field.  
To include a value in your email message body:
```text
{{$parameters.property_name}}
