# Props

Props are inputs passed from a parent component to a child. They let the
parent configure a component with data and behavior, while keeping the child
independent of the parent’s specific state or application logic.

## Passing data

Pass values as JSX attributes. In the component, read them from the props
object, commonly using parameter destructuring:

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

function App() {
  return <Greeting name="Maya" />;
}
```

Props can also be arrays, objects, booleans, and other values. Use meaningful,
specific names so the component’s API is clear at its call site.

## Passing callbacks

A callback prop lets a child notify its parent that something happened. The
parent supplies the function (and usually owns the related state or action);
the child calls it in response to an event:

```jsx
function SaveButton({ onSave }) {
  return <button onClick={onSave}>Save</button>;
}

function Editor() {
  function handleSave() {
    console.log("Saved");
  }

  return <SaveButton onSave={handleSave} />;
}
```

Use event-oriented names such as `onSave` or `onSelect`. If the callback needs
an argument, pass a function that supplies it:

```jsx
function RemoveButton({ itemId, onRemove }) {
  return <button onClick={() => onRemove(itemId)}>Remove</button>;
}
```

This keeps the child reusable: it does not need to know how the parent
implements the action.

## Default values

Set defaults in the destructured function parameter when a prop is optional:

```jsx
function Button({ label = "Submit", disabled = false }) {
  return <button disabled={disabled}>{label}</button>;
}
```

The default is used when the prop is `undefined` or omitted, not when it is
explicitly `null`. Choose defaults that make sense for the component’s
contract; required values should not be disguised with arbitrary defaults.

## Reusable component design

- Accept the data a component needs instead of hard-coding app-specific
  content or state.
- Keep each component focused; use callbacks to communicate events rather
  than embedding parent-specific behavior.
- Prefer a small, clear prop API over many unrelated configuration options.
- Use `children` when callers should provide the component’s content:

  ```jsx
  function Card({ children }) {
    return <section className="card">{children}</section>;
  }

  // <Card><p>Caller-provided content</p></Card>
  ```

Props are read-only from the child’s perspective. Do not mutate them. When a
value needs to change, the parent updates its state and passes the new value
down; this one-way data flow keeps ownership and updates predictable.

## See also

- [Function components](components.md) — component definitions and
  composition.
- [State with `useState`](use-state.md) — state ownership and updates.
- [Back to React fundamentals](README.md)
