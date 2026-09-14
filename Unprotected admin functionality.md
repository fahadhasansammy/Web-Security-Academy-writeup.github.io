# Web Security Academy — Unprotected admin functionality

## Introduction
The **Unprotected admin functionality** lab demonstrates broken access control, where administrative panels or sensitive administrative routes exist within an application without being properly protected by authentication or authorization checks.

---

## Step 1: Mapping the Application and Enumerating Endpoints
1. Access the lab application and use a directory brute-forcing tool, proxy history, or inspect the application's client-side JavaScript files.
2. Review the application code (such as main frontend script files) to see if admin paths or hidden links are referenced in the source.

---

## Step 2: Locating the Hidden Admin Panel
By examining the client-side JavaScript or browsing common administrative paths, you can locate the unprotected administrative endpoint (for example, `/administrator-panel`).

---

## Step 3: Accessing the Admin Panel
Navigate directly to the discovered admin URL in your browser address bar. Because the endpoint lacks proper server-side authentication validation, the panel loads directly without requiring administrator credentials.

---

## Step 4: Deleting Target Users and Completing the Lab
Once inside the unprotected admin panel, locate the interface option to delete users, target the specified user (e.g., `carlos`), and execute the action to complete the lab.
