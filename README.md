# Express.js - Empty req.body on JSON POST Request
This repository demonstrates a common issue in Express.js applications where the request body (req.body) is empty when receiving JSON POST requests.  The problem arises from improper middleware configuration, specifically the missing or incorrectly placed `express.json()` middleware.

The `bug.js` file showcases the problematic code, while `bugSolution.js` provides the corrected version.

## How to Reproduce
1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install` to install dependencies.
4. Run `node bug.js`.
5. Send a POST request to `http://localhost:3000/data` with a JSON payload (e.g., using Postman or curl).
6. Observe that the server logs an empty object for `req.body` in the console.
7. Now, run `node bugSolution.js` and repeat steps 4 and 5.  You'll see that the server now correctly logs the received JSON data.

## Solution
The solution involves ensuring that `express.json()` middleware is correctly placed *before* the route handler that expects a JSON body.  This middleware parses the incoming JSON data and makes it accessible in `req.body`.