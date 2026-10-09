# React terminology

This glossary collects JavaScript and React terms used across the wiki.

## JavaScript syntax

- **Arrow-function syntax** — `parameter => expression` is a concise way to
  write a function. For example,
  `previousCount => previousCount + 1` is equivalent to
  `function (previousCount) { return previousCount + 1; }`. In a state setter,
  React calls this function with the previous state and uses the returned
  value as the next state. See [State with `useState`](react-fundamentals/use-state.md).
- **Object spread syntax** (or **object spread**) — `{ ...previousUser }`
  copies an object's enumerable own properties into a new object. Properties
  written after the spread, such as `name: "Ada"`, override copied properties
  with the same name. This copy is shallow, not a recursive/deep copy. See
  [State with `useState`](react-fundamentals/use-state.md) for immutable state
  update examples.
