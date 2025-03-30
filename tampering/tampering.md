# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

   The code directly incorporates user input into the webpage without proper sanitization or encoding. This leads to a Cross-Site Scripting attack, allowing injected scripts to be executed in the context of the webpage.
2. Briefly explain how a malicious attacker can exploit them.

   An attacker can supply specially crafted input like `<script>...</script>` to inject and run arbitrary JavaScript code. So the innerHTML will be replace with a href with name Gotcha.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?

    It sanitize input. For example, it converts`<` to `&lt;` and `>` to `&gt` , tso that some charatcers are escape and the browser can display the plain text instead of executing it.
