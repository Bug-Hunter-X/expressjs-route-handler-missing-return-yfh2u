# Express.js Route Handler Missing Return Statement

This repository demonstrates a common error in Express.js route handlers: omitting the `return` statement within an `if` condition that handles a scenario like a missing resource.  This can lead to unexpected behavior because subsequent code within the handler will still execute.

## Bug
The `bug.js` file contains the flawed route handler. The `if` block checks for the existence of `userData`. If `userData` is not found, the code should send a 404 response, but the missing `return` allows the following `res.send(userData)` to execute, potentially sending an error or undefined data.

## Solution
The `bugSolution.js` file demonstrates the corrected handler.  Adding `return` before `res.status(404).send()` ensures that if the user is not found, the 404 response is sent, and the rest of the handler is not executed.