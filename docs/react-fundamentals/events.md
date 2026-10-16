# Events

Event handlers let a component respond to user interactions such as clicks,
typing, and form submission. In JSX, event props use camelCase, and you pass
the handler function rather than calling it during rendering:

```jsx
function SaveButton() {
  function handleClick() {
    console.log("Saved");
  }

  return <button onClick={handleClick}>Save</button>;
}
```

`onClick={handleClick}` gives React a function to call when the click happens.
Writing `onClick={handleClick()}` calls the function immediately while
rendering, which is usually not what you want.

## Passing handlers between components

A parent can pass a callback to a child as a prop. The child calls it when
the relevant interaction occurs; the parent can keep ownership of the action
or state:

```jsx
function ItemButton({ item, onSelect }) {
  return (
    <button onClick={() => onSelect(item)}>
      Choose {item}
    </button>
  );
}

function ItemPicker() {
  function handleSelect(item) {
    console.log("Selected:", item);
  }

  return <ItemButton item="book" onSelect={handleSelect} />;
}
```

Use `on...` names for callback props to describe what the child reports, such
as `onSelect` or `onSave`. The parent handler is often named `handle...`,
such as `handleSelect`. This keeps a child reusable and avoids coupling it to
the parent's implementation.

## Event objects and arguments

React passes the event object to a handler. Use it when you need details
about the interaction or its target:

```jsx
function handleClick(event) {
  console.log(event.currentTarget);
}

<button onClick={handleClick}>Inspect button</button>
```

To pass your own argument, use a small function that calls the handler:

```jsx
<button onClick={() => onSelect("book")}>Choose book</button>
```

If you need both the argument and event, accept the event in that function:

```jsx
<button onClick={(event) => onSelect("book", event)}>
  Choose book
</button>
```

## Forms and propagation

Handle form submission with `onSubmit`. Prevent the browser's default page
navigation when the form should be handled by the app:

```jsx
function SearchForm() {
  function handleSubmit(event) {
    event.preventDefault();
    // Read the form data or update application state.
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Search</button>
    </form>
  );
}
```

Many events bubble from the target element to its ancestors. Call
`event.stopPropagation()` only when an ancestor should not also handle that
interaction. Prefer structuring handlers so propagation does not need to be
stopped unnecessarily.

## State updates in handlers

Handlers commonly update state. If the next state depends on the previous
state, use the updater form so the update uses the latest value:

```jsx
setCount(count => count + 1);
```

See [State with `useState`](use-state.md) for state ownership and update
patterns.

## See also

- [Props](props.md) — passing callbacks as component props.
- [State with `useState`](use-state.md) — storing and updating interaction
  state.
- [Back to React fundamentals](README.md)
