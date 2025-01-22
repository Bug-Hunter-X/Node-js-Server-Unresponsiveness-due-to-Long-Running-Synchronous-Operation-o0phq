# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js where a long-running synchronous operation in the request handler blocks the event loop, causing the server to become unresponsive.

## Bug

The `server.js` file contains a simple HTTP server.  The request handler includes a `while` loop that keeps the CPU busy for 5 seconds.  This blocks the event loop, preventing the server from handling subsequent requests during that time.  If you send multiple requests to this server, you'll observe that only the first request is processed, and subsequent requests are queued but never handled. 

## Solution

The `serverSolution.js` file demonstrates a solution using asynchronous operations and promises. This allows the server to continue processing other requests during the long-running task, keeping the server responsive.  The use of `setTimeout` or promises prevents blocking the event loop, maintaining server responsiveness.