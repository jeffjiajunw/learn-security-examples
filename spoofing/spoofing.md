# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

   `$ npx install`
2. Start the **insecure.ts** server

   `npx ts-node insecure.ts`
3. Start the malicious server **mal.ts**

   `npx ts-node mal.ts`
4. Open __http://localhost:8000__ in a browser, type a name and Submit.
5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.
6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.
7. Click the link in the HTML file. Do you see the cookie being stolen in the console?
8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out?

## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
   The application directly use the username to check whether the user name is the admin, it does not check the cookie of samesite and httponly.
2. Briefly explain different ways in which vulnerability can be exploited.
   Attacker trick user browser into making forged requests, as the browser will store session cookies, if the session is set as admin, then when the attacker send requests the browser will still think that the attacker is the user.
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
   Thesession cookie is configured with httpOnly:true and sameSite:true, this prevent XSS attack and block browser from sending cookies CSRF. The session cookies are inaccessible to client-side scripts and not sent on corss-site requests.
