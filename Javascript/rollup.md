# TIL: Rollup

## What is Rollup?

Rollup is a next-generation JavaScript module bundler that compiles small, scattered pieces of code into a single optimized bundle or multiple output chunks.

It is designed primarily for bundling ES modules and is widely used for building JavaScript libraries and applications.

## Key Features

- **Tree Shaking**: Removes unused code from the final bundle, reducing bundle size.
- **Multiple Output Formats**: Supports ES Modules (ESM), CommonJS (CJS), UMD, IIFE, and more.
- **Minimal Code Overhead**: Generates clean and efficient output with very little runtime boilerplate.

## Installation

```bash
npm install rollup --save-dev
```

## Basic Usage

Bundle an entry file into a single ES module output:

```bash
npx rollup src/main.js --file dist/bundle.js --format es
```
