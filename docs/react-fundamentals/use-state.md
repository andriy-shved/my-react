# State with `useState`

`useState` is a React Hook for keeping a state value in a function component.
It returns an array containing the current state value and a setter function.
The argument is the initial state:

```jsx
const [count, setCount] = useState(0);
```

JavaScript array destructuring assigns the two returned values to local names.
Conceptually, this is equivalent to:

```js
const statePair = useState(0);
const count = statePair[0];
const setCount = statePair[1];
```

`count` is the current value for this render. Call `setCount` to request an
update; do not assign to `count` directly:

```jsx
setCount(count + 1);
```

When the next value depends on the previous one, use the updater form:

```jsx
setCount(previousCount => previousCount + 1);
```

React calls the updater function with the latest queued state and uses its
return value as the next state. This is useful when multiple updates may be
queued, because each updater receives the result of the previous update.

## Updating objects and arrays

Treat state as read-only. To update an object or array, create a new value
rather than mutating the existing one. A new reference lets React detect that
the state changed:

```jsx
setUser(previousUser => ({
  ...previousUser,
  name: "Ada",
}));

setItems(previousItems => [...previousItems, newItem]);
```

In the object example, the existing properties are copied and then `name` is
set to `"Ada"` (replacing the old value if present). The array example copies
the current items and appends `newItem`. Avoid changing an existing object and
passing the same reference back to the setter.

Object spread makes a **shallow copy**: nested objects are still shared
references. To update a nested property, copy each object along the path:

```jsx
setUser(previousUser => ({
  ...previousUser,
  address: {
    ...previousUser.address,
    city: "London",
  },
}));
```

## How React knows what to render again

React associates each Hook call with the component currently rendering it.
The setter returned by `useState` is connected to that particular state.
Calling it tells React which state to update, and React schedules the owning
component to render again. React may also render affected descendants.
React compares the next state with the current state using `Object.is`; when
they are equal, it can skip rendering the component's children.

Hook calls must happen in the same order on every render. This is why Hooks
must be called at the top level of a function component or custom Hook—not
conditionally or inside loops. React uses the call order to match each Hook
call to its state across renders.

The setter does not change the `count` variable in the already-running
render. That variable remains the value for that render; React supplies the
updated value during a subsequent render.

## Counter example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(previousCount => previousCount + 1)}>
      Clicked {count} times
    </button>
  );
}
```

The button displays the current state. Clicking it calls the setter, and React
renders `Counter` again so the UI reflects the new value.

## See also

- [Function components](components.md) — component definitions and rendering.
- [Props](props.md) — passing data to components.
- [React terminology glossary](../terminology.md) — syntax terms used in
  these examples.
- [Back to React fundamentals](README.md)
