# EmailJS Setup Guide

This guide explains how to connect the contact form on your website so that messages get delivered to your email inbox.

---

## 1. Create a free EmailJS account

Go to [https://www.emailjs.com](https://www.emailjs.com) and sign up for a free account.

---

## 2. Add an Email Service

1. In your EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail is the easiest)
4. Follow the on-screen steps to connect your account
5. Copy the **Service ID** (looks like `service_xxxxxxx`)

---

## 3. Create an Email Template

1. Go to **Email Templates**
2. Click **Create New Template**
3. Set the **Subject** to:
   ```
   New message from {{name}} — your website
   ```
4. For the **email body**, use the pre-built template included in this project:
   - Click **Edit Content** dropdown inside the template editor
   - Click **Code Editor** (second option in the dropdown)
   - Open the file `email-template.txt` from this project folder
   - Copy the entire contents and paste it into the code editor
   - Click **Apply**
5. Set **To Email** to your own email address
6. Set **Reply To** to `{{email}}` (so you can reply directly to the sender)
7. Click **Save** and copy the **Template ID** (looks like `template_xxxxxxx`)

---

## 4. Get your Public Key

1. Go to **Account** → **General**
2. Copy your **Public Key** (looks like `aBcDeFgHiJkLmNoP`)

---

## 5. Add your keys to the website

Open `assets/js/scripts.js` and find these two lines (around line 95 and 120):

```js
emailjs.init("YOUR_PUBLIC_KEY");
```

```js
.sendForm("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", this)
```

Replace the placeholders with your actual values:

```js
emailjs.init("aBcDeFgHiJkLmNoP"); // ← your Public Key
```

```js
.sendForm("service_xxxxxxx", "template_xxxxxxx", this)  // ← your IDs
```

Save the file and push the changes to GitHub.

---

## Done ✅

Test it by filling out the contact form on your website. You should receive the message in your inbox within a few seconds.

> **Free plan limits:** EmailJS free tier allows up to 200 emails per month, which is plenty for a portfolio site.
