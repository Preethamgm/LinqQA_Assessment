# 🧪 QA Analyst Take-Home – Linq Contact Exchange Flow

By Preetham Ganumpalli Mekala

This project contains a manual QA assessment of the **contact exchange flow** on [Linq's public profile page](https://linqapp.com/daniela). It includes test cases, bug reports, exploratory insights, and API testing using DevTools and Postman/Python.

---

## 📁 Folder Structure

```
.
├── test-cases.md           # List of detailed manual test scenarios
├── bugs.md                 # Reported issues and findings
├── postman-notes.md        # API/DevTools analysis and rate-limit testing
├── screenshots/            # Supporting screenshots for bugs and tests
├── README.md               # This file
```

---

## ✅ Scope of Testing

- Tested **public visitor flow**: visit a Linq profile and exchange contact info
- Verified form validations for **email**, **phone**, and **name**
- Downloaded `.vcf` contact card to check access behavior
- Inspected API requests using **DevTools**, **Postman**, and a **Python script**
- Explored potential for **abuse**, **spam**, and **data integrity issues**

---

## 🧪 Highlights of What I Tested

- Valid + invalid form submissions
- Unicode/emoji input handling
- Duplicate contact handling
- Downloading contact info without providing your own
- API call structure, headers, payload, and backend response
- Rate-limiting (or lack thereof)
- Absence of CAPTCHA or bot detection

---

## 🐞 Key Bugs & Concerns Logged

- No rate-limiting on `POST /user_contacts` (critical)
- Public contact download without visitor verification
- Fake/disposable emails (e.g., `testcase@fake.com`) accepted as real
- Duplicate email submissions allowed without warning
- Excessively long name input (700+ chars) accepted
- No bot protection or CAPTCHA present

📂 See `bugs.md` for full descriptions and screenshots.

---

## 🔧 Suggested QA Improvements

If I joined as the first QA hire at Linq, I would:
1. Implement API-level rate-limiting and CAPTCHA protection
2. Introduce automated regression testing for key flows
3. Improve backend validation and input sanitization

🧠 See `postman-notes.md` and bug logs for more details.

---

## 🤝 Thank you!

This QA take-home was completed with a focus on **clarity, depth, and real-world impact**. I'm excited about the opportunity to bring thoughtful testing and process improvements to Linq’s growing team.
```
