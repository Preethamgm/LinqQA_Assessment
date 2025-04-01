# 📄 Test Cases - Contact Exchange Flow (Linq)

| Test Case ID | Description                                      | Steps                                                                                     | Expected Result                                                                 |
|--------------|--------------------------------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| TC-01        | Valid form submission with email                 | 1. Enter valid name <br> 2. Enter valid email <br> 3. Click "Continue"                    | Contact is saved and confirmation message is shown                              |
| TC-02        | Valid form submission with phone number          | 1. Enter valid name <br> 2. Enter valid phone number <br> 3. Click "Continue"             | Contact is saved and confirmation message is shown                              |
| TC-03        | Missing name field                               | 1. Leave name field blank <br> 2. Fill in valid email <br> 3. Click "Continue"            | Error message: "Name is required"                                               |
| TC-04        | Missing both phone and email                     | 1. Enter name <br> 2. Leave both phone and email blank <br> 3. Click "Continue"           | Error message: "Either phone or email is required"                              |
| TC-05        | Invalid email format                             | 1. Enter name <br> 2. Enter "test@" or "abc@com" as email <br> 3. Click "Continue"        | Error message: "Please enter a valid email"                                     |
| TC-06        | Invalid phone number                             | 1. Enter name <br> 2. Enter "000" or "123" <br> 3. Click "Continue"                       | Error message: "Enter a valid phone number"                                     |
| TC-07        | Submitting form multiple times with same email   | 1. Enter valid name and email <br> 2. Submit form 3 times                                | Contact is saved repeatedly; no deduplication message                           |
| TC-08        | Long name input (788+ characters)                | 1. Enter 788+ character name <br> 2. Enter valid email <br> 3. Submit                     | Form is submitted without error                                                 |
| TC-09        | Name with emojis and special characters          | 1. Enter name like "John 😊" or "محمد" <br> 2. Enter valid email <br> 3. Submit            | Form accepts name without any validation error                                  |
| TC-10        | Open contact download link without login         | 1. Visit public Linq contact link <br> 2. Click "Download Contact"                       | Contact info (.vcf file) is downloaded without verification                     |
| TC-11        | Network errors handling                          | 1. Disconnect internet <br> 2. Fill valid form <br> 3. Click "Continue"                   | Form shows appropriate network error message                                    |
| TC-12        | Check API rate-limiting                          | 1. Submit the same form via script in quick succession (20+ requests in 5 sec)           | No rate-limiting enforced; all requests accepted                                |
| TC-13        | No CAPTCHA/spam protection check                 | 1. Submit form using automation <br> 2. Observe form behavior                             | No CAPTCHA shown; submission still successful                                   |
| TC-14        | Inspect DevTools for security issues             | 1. Open DevTools > Network/Console <br> 2. Submit form                                    | Exposed endpoints, missing protections, deprecated warnings observed            |
| TC-15        | Invalid API access (direct)                      | 1. Visit `https://api.linqapp.com/user_contacts` directly in browser                     | Error shown: "Page you are looking for doesn’t exist"                           |

---

📌 _Note: Actual results and screenshots were collected during manual testing and will be provided separately._
