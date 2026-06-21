# Today I Learned - JSDoc

## What is JSDoc?

JSDoc is a standard way to document JavaScript and TypeScript code using comments.

Benefits:

- Explains function purpose
- Documents parameters and return values
- Improves IDE autocomplete and hints
- Makes code easier to understand and maintain

## Basic Example

```ts
/**
 * Generates a random short code.
 *
 * @param length Length of the generated code.
 * @returns Random alphanumeric short code.
 */
function generateShortCode(length = 6): string {
  // implementation
}
```

## Common Tags

| Tag | Purpose |
|------|---------|
| `@param` | Documents a function parameter |
| `@returns` | Documents the return value |
| `@example` | Shows usage examples |
| `@throws` | Documents possible errors |
| `@deprecated` | Marks code as deprecated |

## Example with Multiple Parameters

```ts
/**
 * Creates a short URL entry.
 *
 * @param url Original URL to shorten.
 * @param shortCode Generated short code.
 * @returns Created ShortUrl object.
 */
function createShortUrl(
  url: string,
  shortCode: string
): ShortUrl {
  // implementation
}
```

## Key Lesson

Good comments explain **why** something exists.

Good JSDoc explains:

- What a function does
- What it accepts
- What it returns

The function implementation should explain **how** it works.
