# Firebase Cloud Functions: Unexpected null in context.auth

This repository demonstrates an uncommon error in Firebase Cloud Functions where `context.auth` unexpectedly returns `null` instead of `undefined` when an HTTPS Callable function is invoked without authentication.  This behavior differs from the typical undefined return, causing issues in error handling.

The `bug.js` file shows the problematic code.  The solution (`bugSolution.js`) provides a correct way to handle this unexpected null case.

## Problem

Standard Firebase documentation suggests that `context.auth` would be `undefined` if the function is called without authentication.  However, in some scenarios, it can unexpectedly return `null`. This leads to runtime errors since checking for `!context.auth` fails when `context.auth` is `null`.

## Solution

The solution utilizes a strict equality check (`===`) to correctly handle both `undefined` and `null` cases, providing robust error handling and preventing runtime crashes.