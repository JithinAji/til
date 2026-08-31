# JavaScript: Why a Missing Semicolon Can Throw an Array Error

## The Code

```js
let a = [1, 2]
[3, 4].forEach(console.log)
```

This looks like two separate statements:

1. Create an array and store it in `a`.
2. Print each value in a second array.

But JavaScript does not always treat the line break as the end of a statement.

## How JavaScript Reads It

Because the second line starts with `[`, JavaScript can continue the first expression. It interprets the code like this:

```js
let a = [1, 2][3, 4].forEach(console.log)
```

The `[3, 4]` part is treated as bracket property access on `[1, 2]`.

Inside bracket property access, `3, 4` is the comma operator: it evaluates both values and produces the final value, `4`.

So JavaScript effectively tries to do this:

```js
let a = [1, 2][4].forEach(console.log)
```

`[1, 2][4]` is `undefined`, because the array has no item at index `4`. Calling `.forEach` on `undefined` throws an error similar to:

```text
TypeError: Cannot read properties of undefined (reading 'forEach')
```

## The Fix

End the first statement with a semicolon:

```js
let a = [1, 2];
[3, 4].forEach(console.log)
```

Now the code is unambiguously two statements, and it prints:

```text
3
4
```

## Alternative Style

If your project does not use semicolons, put a defensive semicolon before any line that begins with `[`:

```js
let a = [1, 2]
;[3, 4].forEach(console.log)
```

## Key Takeaway

JavaScript's automatic semicolon insertion does not insert a semicolon when the next line can validly continue the current expression. Lines beginning with `[` are one of the common cases where this can cause a surprising error.

