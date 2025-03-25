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
- Using the user input directly and not sanitizing
- Could find an admin
- No authorization validation to ensure the right person is escalating

2. Briefly explain how a malicious attacker can exploit them.
- Attacker that isn't logged in can change the role of any user without authentication
- Attacker can access any user name through input manipulation ex. { "$ne" :  null}

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
- Extends session data to include userId and checks log-in info
- Finds user based on log-in info and not user input