# Web Security Academy — User role modified in user profile

## Introduction
The **User role modified in user profile** lab illustrates Broken Object Property Level Authorization (BOPLA) or mass assignment vulnerabilities, where users can manipulate internal profile parameters (like role identifiers) during updates to elevate their privileges.

---

## Step 1: Logging In and Intercepting Traffic
1. Log in to the application using your assigned standard user credentials.
2. Turn on your intercepting proxy (such as Burp Suite) and navigate to your user account profile page.

---

## Step 2: Updating Account Details
1. Edit your profile details (such as your email address) and click **Update profile** while your proxy is intercepting the HTTP request.
2. Inspect the JSON payload or form parameters sent in the POST/PUT request. Notice if additional parameters are present or can be injected, such as `"roleId": 1` or `"role": "admin"`.

---

## Step 3: Modifying the Role Parameter
1. Modify the parameter controlling your user role (for example, change `"roleId": 2` representing a standard user to `"roleId": 1` or `"role": "admin"` representing an administrator).
2. Forward the modified request to the server.

---

## Step 4: Verifying Privilege Elevation and Completing the Lab
Refresh your profile or navigate to the administrative section of the application. If the backend accepts the modified property without validating authorization, your account role will be updated to administrator, completing the lab.
