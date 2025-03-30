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
- The user input taken in /register is not sanitized.
- There is no security/authentication for Admin

2. Briefly explain how a malicious attacker can exploit them.
- Because the user input is not sanitized, attackers can insert malicious urls that will redirect vulnerable website users to harmful links.
- An attacker can access Admin log-in and easily find the /sensitive url by impersonating other users
- session hijacking

3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
- This sanitized the user input to eliminate possibility of malicious scripts etc.
