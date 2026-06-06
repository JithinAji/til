# TIL: JavaScript Namespaces

A namespace is a way to group related functions, variables, or classes under a single name to avoid conflicts and keep code organized.

## Without a Namespace

```js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}
```

As a project grows, having many global functions can lead to naming conflicts and make the code harder to navigate.

## Using an Object as a Namespace

```js
const MathUtils = {
  add(a, b) {
    return a + b;
  },

  subtract(a, b) {
    return a - b;
  }
};

console.log(MathUtils.add(2, 3));      // 5
console.log(MathUtils.subtract(5, 2)); // 3
```

Here, `MathUtils` acts as a namespace. Related functions are grouped together and accessed through the object.

## Modern Approach: ES Modules

Today, JavaScript modules provide namespacing automatically.

```js
// math.js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

```js
// app.js
import * as MathUtils from "./math.js";

MathUtils.add(2, 3);
MathUtils.subtract(5, 2);
```

## Key Takeaway

A namespace is simply a container for related code.

```js
const MathUtils = {
  add() {},
  subtract() {}
};
```

This helps organize code and prevents naming conflicts.
