# 🧪 Postman & DevTools Notes – Linq Contact Exchange

---

## 🔍 How I Inspected the API

1. **Opened Chrome DevTools → Network tab**
2. Visited a public Linq profile: `https://linqapp.com/daniela`
3. Clicked “Exchange Contact” and submitted valid contact details (name + email)
4. Observed API calls made to `https://api.linqapp.com/api/v2/user_contacts`

---

## 📡 Request Details

### ➤ Endpoint:
```
POST https://api.linqapp.com/api/v2/user_contacts
```

### ➤ Headers:
```http
Content-Type: application/json
```

### ➤ Payload (copied from browser request):
```json
{
  "contact_id": 2265350,
  "user_id": 25683,
  "form_fields_attributes": [],
  "created_from_card_id": 26456,
  "is_accept_marketing": false
}
```

### ➤ Response (example):
```json
{
  "data": {
    "user_contact": {
      "id": 3206809,
      "contact_id": 2265350,
      "user_id": 25683,
      ...
      "created_from_name": "Daniela"
    }
  }
}
```

---

## 📬 Postman / Python Testing

Used Postman and Python script to simulate 20+ rapid submissions to the same endpoint using the exact payload.

All requests returned:
```
Status: 200 OK
```

---

## ⚠️ Key Findings & Concerns

### 🔓 1. No Rate Limiting
- Submitted the same contact data 20+ times within seconds
- All returned `200 OK`
- **Concern**: This allows automated abuse and spam

### ❌ 2. No CAPTCHA or Bot Detection
- No visible bot protection when submitting via script
- Could easily be exploited via automation

### 🗂 3. No Deduplication
- Same email submitted repeatedly with no error or warning
- Backend accepted identical contact info each time

### 📄 4. Download Contact Without Verification
- `.vcf` file can be downloaded without entering any personal data or authentication
- Could lead to mass scraping of contact data

### 🛠 5. Poor Error Handling on Direct Access
- Accessing `https://api.linqapp.com/user_contacts` in browser gives vague error
- No clear 403/401 or JSON-formatted response for bad access

---

## 🤔 Questions for the Team

- Should public contact downloads require CAPTCHA or visitor info first?
- Are there plans to implement backend deduplication or rate limits?
- Is there any protection against automated contact scraping?
- Can form field validation be strengthened (e.g., character limits)?

---

✅ All of these were discovered using Chrome DevTools, Postman, and Python scripting during exploratory QA testing.
