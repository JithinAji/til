# TIL: `Object.prototype.hasOwnProperty.call()` vs `obj.hasOwnProperty()`

When checking if an object has a property, you may see two patterns:

```js
obj.hasOwnProperty('name');
```

and

```js
Object.prototype.hasOwnProperty.call(obj, 'name');
```

## Why use `Object.prototype.hasOwnProperty.call()`?

`obj.hasOwnProperty()` assumes that the object has a valid `hasOwnProperty` method.

However, an object can override or remove it:

```js
const obj = {
  hasOwnProperty: () => false,
  name: 'Aji',
};

obj.hasOwnProperty('name'); // false ❌
```

Using `Object.prototype.hasOwnProperty.call()` always uses the original method from `Object.prototype`:

```js
Object.prototype.hasOwnProperty.call(obj, 'name'); // true ✅
```

## Another Example

Objects created without a prototype do not have `hasOwnProperty` at all:

```js
const obj = Object.create(null);

obj.name = 'Aji';

obj.hasOwnProperty('name'); // TypeError ❌

Object.prototype.hasOwnProperty.call(obj, 'name'); // true ✅
```

## Rule of Thumb

Use:

```js
Object.prototype.hasOwnProperty.call(obj, key);
```

when working with unknown objects, as it is safer and more reliable.
