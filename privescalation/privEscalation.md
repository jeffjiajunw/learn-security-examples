# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
   It just check whether the userid role is admin, but the userid is provided mby client, so it can be guessed. And there is no session or token authentication.
2. Briefly explain how a malicious attacker can exploit them.
   An attacker can craft a request that includes the `userId` of an admin, even if they are not an admin themselves. It change the admin role.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
   The server checks for a valid session to check if user is authenticated instead of let user provide the id itself. It will check if user is admin. The session cookies are configured with httponly and samesite strict to prevent from csrf attack.
