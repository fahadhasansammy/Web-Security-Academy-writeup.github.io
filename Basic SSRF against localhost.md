# Web Security Academy — Basic SSRF against localhost

## Introduction
The **Basic SSRF against localhost** lab demonstrates Server-Side Request Forgery (SSRF), a vulnerability where an application can be manipulated to issue server-side HTTP requests to an arbitrary internal target system or loopback address (`localhost`).

---

## Step 1: Analyzing Application Features with Outbound Requests
1. Log in to the lab and browse product pages. Notice features that interact with external URLs or fetch remote data, such as a "Check stock" feature.
2. Intercept the stock check request using Burp Suite to see how the stock API communicates with internal services.

---

## Step 2: Identifying the URL Parameter
The stock check function sends a POST request containing a stock check URL parameter pointing to an internal stock checking API, such as:
`stockApi=http://stock.welleval.local/product?stock=1`

---

## Step 3: Exploiting SSRF against Localhost
1. Modify the `stockApi` parameter value to target the local loopback address and the administrative endpoint (for example, `http://localhost/admin/`).
2. Send the request to check if the server fetches and returns internal application data from its own local interface.

---

## Step 4: Deleting the Target User
Update the path to target the admin deletion function on localhost (e.g., `http://localhost/admin/delete?username=carlos`) and send the request through the server to complete the lab.
