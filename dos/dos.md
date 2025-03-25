# Denial-of-Service (DoS)

This example demonstrates DoS vulnerabilities and how they can be exploited.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Ignore if you have already done this once. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

    `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?id[$ne]=
    ```

4. Do you see the server crashing?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts** that can lead to a DoS attack.
- There is no rate limiter to stop a lot of requests.
- If the id format entered is invalid, the site crashes

2. Briefly explain how a malicious attacker can exploit them.
- Without a rate limiter, a malicious attacker can send an unlimited amount of requests to the server which can slow down the server or crash it
- A malicious attacker can enter many invalid id formats that will cause extensive CPU usage and increased memory.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the DoS vulnerability?
- This file adds a rate limiter that prevents users from sending to many requests at once. 
- If the id format entered is not valid, the try/catch block will catch this error and return an error status.