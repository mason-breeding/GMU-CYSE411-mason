# CYSE 411 – Instructor Solution (Unit 2.4)
Secure Coding: CSRF, Authentication, and Logic Abuse

---

## 🎯 Purpose of This Version

This is the **secure instructor solution** for the Unit 2.4 homework.

It demonstrates:

- How vulnerabilities manifest in real systems
- How to fix them using **defensive coding principles**
- Why each fix is necessary

All fixes are **implemented and commented in the code**, and explained here.

---

# 🧠 Key Concept

> Security failures occur when systems trust the client, the session, or the workflow without proper validation.

---

# 🔍 Vulnerabilities and Fixes

---

## 1️⃣ CSRF (Cross-Site Request Forgery)

### ❌ Problem

The vulnerable version allowed requests like:

```http
POST /transfer

```

without verifying:

- where the request came from

- whether the user intended the action

Because:

- the browser automatically sends session cookies


### ✅ Fix Implemented

```JavaScript

if (req.body.csrfToken !== req.session.csrfToken)

```

✔ Explanation

- A random token is generated and stored in the session

- The same token must be sent in the request

- Attackers cannot guess this token

📌 Key Insight: CSRF is not about stealing credentials — it is about abusing trusted requests.

🔗 Reference: https://www.npmjs.com/package/csurf

