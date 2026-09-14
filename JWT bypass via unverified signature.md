# Web Security Academy — JWT bypass via unverified signature

## Introduction
The **JWT bypass via unverified signature** lab demonstrates insecure JSON Web Token (JWT) handling, where an application accepts tokens signed with an unverified or weak signature, allowing attackers to tamper with claim values.

---

## Step 1: Logging In and Capturing the JWT
1. Log in to the lab using the provided user credentials.
2. Intercept your web traffic using Burp Suite and observe the `session` cookie or authorization header, which contains a JSON Web Token (JWT).

---

## Step 2: Decoding the JWT
1. Send the request containing the JWT to Burp Repeater or use a JWT editor extension.
2. Inspect the JWT structure consisting of three parts separated by dots: Header, Payload, and Signature. The payload contains claims like your username and administrative status (e.g., `"sub": "wiener"`, `"admin": false`).

---

## Step 3: Modifying Claims and Handling the Signature
1. Change the claim inside the payload section (for example, change `"admin": false` to `"admin": true` or change the username to `administrator`).
2. Depending on how the application handles signatures, either strip the signature entirely, modify the header algorithm to `none`, or re-sign the token if a static or blank secret key is used.

---

## Step 4: Accessing the Admin Interface
Send the request with the modified JWT to the server. Because the application fails to properly cryptographically verify the token signature, it trusts the tampered payload, granting administrative access and completing the lab.
