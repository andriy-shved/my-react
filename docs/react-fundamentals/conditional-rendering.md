# Conditional rendering

Conditional rendering means choosing which UI React renders based on values
such as props or state. Since a function component is JavaScript, use normal
JavaScript control flow and expressions to decide what JSX to return.

## Choose between UI states

Use `if` statements when a condition changes a substantial part of the UI.
Early returns make distinct states, such as loading, error, empty, and success,
easy to see:

```jsx
function Profile({ user, isLoading, error }) {
  if (isLoading) {
    return <p>Loading profile…</p>;
  }

  if (error) {
    return <p role="alert">Could not load profile.</p>;
  }

  if (!user) {
    return <p>No profile found.</p>;
  }

  return <h1>{user.name}</h1>;
}
```

Order checks so unavailable or exceptional states are handled before the
component reads data that may not exist.

## Choose between alternatives

A ternary expression is useful for two concise alternatives:

```jsx
function Greeting({ isSignedIn }) {
  return isSignedIn
    ? <p>Welcome back!</p>
    : <p>Please sign in.</p>;
}
```

For several alternatives, prefer `if` statements or extract a component
rather than nesting ternaries. Overly complex expressions make it harder to
understand which UI appears for each case.

## Render an element optionally

Use `&&` when an element should appear only when a condition is true:

```jsx
function CartNotice({ itemCount }) {
  return (
    <div>
      {itemCount > 0 && <p>You have items in your cart.</p>}
    </div>
  );
}
```

Be explicit when the condition is numeric. In JavaScript, `0 && expression`
evaluates to `0`, and React renders that number. A comparison such as
`itemCount > 0` produces a boolean and avoids accidentally displaying zero.
Use a ternary if the no-content case should be explicit:

```jsx
{itemCount > 0 ? <p>{itemCount} items</p> : null}
```

React renders `null` as no content. It also omits `false` and `undefined` from
the rendered output.

## Let state control what is rendered

When state changes, React renders the component again and evaluates its
conditions using the new state:

```jsx
import { useState } from "react";

function Details() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <section>
      <button
        aria-expanded={isOpen}
        onClick={() => setIsOpen(open => !open)}
      >
        {isOpen ? "Hide details" : "Show details"}
      </button>

      {isOpen && <p>Additional information goes here.</p>}
    </section>
  );
}
```

The `aria-expanded` value communicates the disclosure state to assistive
technology. Conditional rendering can change content and controls as well as
purely visual details.

## Unmounting versus hiding

When a condition removes a component from the rendered tree, React unmounts
it. Its local state is discarded and its effects are cleaned up. If it is
rendered again, it starts with fresh state.

Hiding a still-rendered component with CSS, for example with
`display: none`, does not unmount it: its state and effects remain active.
Choose based on the desired behavior. Unmounting can stop work in a closed
panel, while keeping a component mounted can preserve an unfinished form.

## Practical guidance

- Make important states explicit, especially loading, error, empty, and
  success states.
- Write conditions that clearly express the intended boolean, such as
  `itemCount > 0`.
- Keep conditional JSX readable; extract a component when a branch becomes
  large or has its own responsibility.
- Call Hooks at the top level of a component or custom Hook, never inside a
  condition or loop. Conditionally render UI that uses Hook values instead.
- If only the appearance should change, use styling rather than mounting and
  unmounting elements.

## See also

- [JSX basics](jsx.md) — embedding JavaScript expressions in JSX.
- [Props](props.md) — passing values that can determine what a child renders.
- [State with `useState`](use-state.md) — updating state that drives the UI.
- [Events](events.md) — responding to interactions that change state.
- [Back to React fundamentals](README.md)
