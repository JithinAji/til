# Today I Learned: Measuring Code Execution with `performance.mark()` and `performance.measure()`

Today I learned how to accurately measure the execution time of JavaScript code using the **Performance API**.

Instead of relying on `console.time()`, the Performance API allows you to create named timestamps and measure the duration between them with high precision.

## Example

```javascript
performance.mark("start");

// Some expensive work
for (let i = 0; i < 100000000; i++) {}

performance.mark("end");

performance.measure(
  "Loop Execution",
  "start",
  "end"
);

const measures = performance.getEntriesByType("measure");

console.log(measures[0].duration); // e.g. 312.56 ms
```

## How it works

1. `performance.mark("start")` records the starting timestamp.
2. Execute the code you want to measure.
3. `performance.mark("end")` records the ending timestamp.
4. `performance.measure()` calculates the duration between the two marks.
5. `performance.getEntriesByType("measure")` returns the recorded measurements.

## Why use it?

- High-precision timing.
- Measure synchronous and asynchronous operations.
- Great for profiling expensive functions.
- Useful when optimizing application performance.
- Integrates with `PerformanceObserver` for automatic performance monitoring.

## Takeaway

The Performance API makes it easy to replace assumptions with measurements. Before optimizing a piece of code, measure it. The slowest function is often not the one you expected.
