# Twilio OTP Authentication in CodeIgniter 4

This project implements **OTP-based authentication** using **Twilio Verify API** in a CodeIgniter 4 application.\
Users can request an OTP via SMS and verify it for authentication.

---

## 🚀 Features

- Send OTP via Twilio
- Verify OTP for authentication
- Uses **Twilio Verify API**
- Supports **E.164 phone number format**
- Includes a **view file** for user interaction
- `.env` file for Twilio configuration

---

## 🛠️ Installation Steps

### 1️⃣ Clone the Repository

```sh
git clone https://github.com/Shahil74/otp_based_verification_php.git
cd otp_based_verification_php
```

### 2️⃣ Install Dependencies

```sh
composer install
```

### 3️⃣ Configure Twilio in `.env` File

1. **Sign up or log in** to [Twilio Console](https://www.twilio.com/console).
2. Get your **Twilio Credentials**:
   - **Account SID**
   - **Auth Token**
   - **Verify Service SID**
3. Open the `.env` file and add:

```
TWILIO_ACCOUNT_SID="YOUR_TWILIO_ACCOUNT_SID"
TWILIO_AUTH_TOKEN="YOUR_TWILIO_AUTH_TOKEN"
TWILIO_VERIFY_SID="YOUR_TWILIO_VERIFY_SERVICE_SID"
```

### 4️⃣ Set Up Environment

Rename `.env.example` to `.env` and update:

```
CI_ENVIRONMENT = development
```

### 5️⃣ Start the Development Server

```sh
php spark serve
```

---

## 🖥️ UI (View File)

This project includes a frontend view for users to enter their phone number and OTP.

### **View File Location:**

```
app/Views/otp_view.php
```

This file contains a simple **HTML form** where users enter their phone number and OTP.

---

## 🛁 API Endpoints

### **1️⃣ Send OTP**

- **URL:** `/send-otp`
- **Method:** `POST`
- **Payload:**

```json
{
  "phone": "+1234567890"
}
```

- **Response:**

```json
{
  "status": "pending",
  "message": "OTP sent successfully"
}
```

---

### **2️⃣ Verify OTP**

- **URL:** `/verify-otp`
- **Method:** `POST`
- **Payload:**

```json
{
  "phone": "+1234567890",
  "otp": "123456"
}
```

- **Response (Success):**

```json
{
  "status": "success",
  "message": "OTP verified successfully"
}
```

- **Response (Failure):**

```json
{
  "status": "error",
  "message": "Invalid OTP"
}
```

---

## 🛠️ Troubleshooting

### ❌ `Twilio Error: Permission to send an SMS has not been enabled`

👉 **Fix:**

1. Enable **SMS Geo-Permissions** for your country:\
   [Twilio SMS Geo-Permissions](https://www.twilio.com/console/sms/settings/geo-permissions)
2. Ensure the phone number is in **E.164 format** (`+91XXXXXXXXXX`).
3. If using a free Twilio account, **verify the recipient number** in:\
   [Twilio Verified Caller IDs](https://www.twilio.com/console/phone-numbers/verified)

---






