# Web Exploitation — PortSwigger / Access Control: User ID controlled by request parameter

## Introduction
The **User ID controlled by request parameter** vulnerability (commonly referred to as an Insecure Direct Object Reference or IDOR) occurs when an application uses user-supplied input to directly access objects or records without verifying whether the currently logged-in user has authorization to view them.



## Step 1: Logging In and Intercepting Traffic
1. Access the lab application and log in using your assigned credentials (for instance, the standard user account provided in the lab details).
2. Configure your intercepting proxy (such as Burp Suite) to intercept web traffic.
3. Click on your profile or account page to observe how the application requests user-specific data.



## Step 2: Identifying the IDOR Vulnerability
When navigating to your user profile page, notice the URL structure or parameter handling passes a direct identifier, such as:

`https://vulnerable-website.com/my-account?id=123`

The application retrieves and displays account details based entirely on the `id` parameter value supplied in the request, without checking if the session user matches that ID.



## Step 3: Modifying the Request Parameter
1. In your proxy history or browser address bar, change the user identifier parameter to target another user account (for example, changing `id=123` to `id=1` or `id=2` to target an administrator or another user).
2. Send the modified request to the server.



## Step 4: Accessing Unauthorized Data and Completing the Lab
Because the application lacks proper server-side access controls for the object reference, it responds with the target user's account details and sensitive information (such as password or API keys), allowing you to successfully bypass authorization constraints.
