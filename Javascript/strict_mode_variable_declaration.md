# Undeclared Variables Behave Differently in Strict Mode

## The gotcha

In JavaScript, assigning a value to an identifier without declaring it can behave differently depending on whether **strict mode** is enabled.

### Non-strict mode

```js
// no "use strict"

num = 5;

console.log(num); // 5
```

In non-strict mode, if `num` doesn't already exist, this assignment can create a property on the global object.

### Strict mode

```js
"use strict";

num = 5;
// ReferenceError: num is not defined
```

Strict mode prevents accidental creation of global variables, so the assignment throws a `ReferenceError`.

## Why this matters

Accidentally creating globals can cause:

- unexpected shared state
- hard-to-track bugs
- name collisions
- code that behaves differently depending on execution context

The safe practice is simple: **always declare variables explicitly.**

```js
const num = 5;
```

## Takeaway

> **Undeclared assignment may create a global in sloppy mode, but throws a `ReferenceError` in strict mode.**

Prefer explicit declarations with `const`, `let`, or `var`.
