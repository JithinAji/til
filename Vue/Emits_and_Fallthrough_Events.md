t is `emits`?

In Vue 3, a component can explicitly declare the events it emits using the `emits` option.

```js
emits: ['click', 'change']
`````

This tells Vue:

> These are component events handled through `$emit()`.

---

## Why does this matter?

If a parent uses:

```vue
<MyComponent @click="handleClick" />
`````

but `click` is **not declared** in the component's `emits`, Vue can treat the listener as a **fallthrough attribute**.

For a component with a single root element, the listener may be attached to that root DOM element.

This is normally useful because Vue allows attributes and listeners to fall through components automatically.

However, it can cause problems if the component also manually emits the same event.

### Without `emits`

```text
Physical click
     │
          ├──> Root DOM @click
               │       └──> Parent handler
                    │
                         └──> Component handler
                                      └──> $emit('click')
                                                           └──> Parent handler
                                                           `````

                                                           The parent handler can be triggered twice.

                                                           ---

                                                           ## With `emits`

                                                           Declare the event:

                                                           ```js
                                                           emits: ['click']
                                                           `````

                                                           Now Vue knows that `click` is a **component event**.

                                                           The event flow becomes:

                                                           ```text
                                                           Physical click
                                                                 ↓
                                                                 Component handler
                                                                       ↓
                                                                       $emit('click')
                                                                             ↓
                                                                             Parent @click
                                                                             `````

                                                                             The listener is handled as a component event instead of falling through to the root DOM element.

                                                                             ---

                                                                             ## General Rule

                                                                             If a component uses:

                                                                             ```js
                                                                             this.$emit('someEvent')
                                                                             `````

                                                                             declare the event in:

                                                                             ```js
                                                                             emits: ['someEvent']
                                                                             `````

                                                                             This makes the component's event API explicit and avoids unintended fallthrough behavior.

                                                                             ## Key Takeaway

                                                                             **Props come into a component. Events go out of a component.**

                                                                             Declaring `emits` tells Vue which events intentionally belong to the component rather than being treated as fallthrough listeners.

                                                                             ````
                                                                             ````
                                                                             ````
                                                           ````
                                                           ````
````
````
