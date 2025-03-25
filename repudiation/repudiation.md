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
- There is no authentication. Any use can send or receive messages
- There is no logging of requests

2. Briefly explain why the vulnerability is addressed in __secure.ts__.
- The vulnerability is addressed to prohibited unauthorized users from accessing messages without authentication
- Logging errors allows for the system to catch attackers that try to modify information without being detected
- Errors are being monitored and added to log for better tracking

3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
- The Middleware pattern. It has preprocessing middleware, authentication middleware, error-handling middleware, and logging middleware. Each middlware sections handles a section of the server to improve the readability of the code.