# React: Objects are not valid as a child

## Problem

Rendering a plain object in JSX throws:

"Objects are not valid as a React child"

## Example
```
/*
   data = {
     a: 3,
       b: 4
       
   }
   */

export const DisplayJSON = ({ data  }) => {
  return <pre>{data}</pre> // ❌ Error
}
```

## Why

React can only render:
- strings
- numbers
- arrays of renderable values
- React elements

Plain objects are not directly renderable.

## Fix

Convert the object into a string:

<pre>{JSON.stringify(data, null, 2)}</pre>

## Note

Arrays like [1, 2, 3] work because React renders each item individually.
Arrays are mainly used for rendering lists with `.map()`.
"
