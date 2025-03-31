# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`
2. Run the server __insecure.ts__.
3. Pretend to be a malicous user and interact with the services by sending requests from the browser.
4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
   The web does not verfiy user identity so that they cannot prove which user send a particular message.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
   Every message sent is logged with timestamp and IP address to the persistent file. Also, it require user to be authenticated to receive messages.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
   It use chain of responsibility. Each function in middleware process the request sequentially. If the function can't completely handle the request, it passes the control to the next func.
