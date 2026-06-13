# .nvmrc

## What is `.nvmrc`?

A `.nvmrc` file specifies the Node.js version a project should use when working with **NVM (Node Version Manager)**.

It helps ensure all developers use the same Node.js version, reducing "works on my machine" problems.

## Example

```text
22
```

This tells NVM to use Node.js 22.

You can also specify an exact version:

```text
22.17.0
```

Or always use the latest LTS version:

```text
lts/*
```

## Usage

Create a file named `.nvmrc` in the project root:

```bash
echo "22" > .nvmrc
```

Then run:

```bash
nvm use
```

NVM will automatically switch to the version specified in the file.

## Why use it?

- Consistent development environments
- Fewer version-related bugs
- Easier onboarding for new developers
- Works well with CI/CD pipelines

## Recommendation

For most projects:

```text
22
```

Pinning the major LTS version provides stability while still allowing minor and patch updates.
