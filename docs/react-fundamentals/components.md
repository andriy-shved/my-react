# Function components

A function component is a JavaScript function that returns JSX. Component
names begin with a capital letter, and components are used with JSX tags:

```jsx
function Greeting() {
  return <h1>Hello!</h1>;
}

function App() {
  return <Greeting />;
}
```

`<Greeting />` is a component element. React invokes the component as part of
rendering; normally, do not call it directly as `Greeting()`.

## Props

Props are inputs passed to a component. They let you reuse a component with
different data; treat them as read-only. See [Props](props.md) for passing
data and callbacks, setting defaults, and designing reusable component APIs.

## Exporting and importing

Export a component from its module so another file can import and use it.
With a named export, import it using braces and the same name:

```jsx
// Greeting.jsx
export function Greeting() {
  return <h1>Hello!</h1>;
}

// App.jsx
import { Greeting } from "./Greeting";
```

A module can instead have one default export. Its import has no braces and
can choose its local name:

```jsx
// Greeting.jsx
export default function Greeting() {
  return <h1>Hello!</h1>;
}

// App.jsx
import WelcomeMessage from "./Greeting";
```

Follow the export style used by the project. Named exports are useful when a
module exposes multiple named values; a default export is often used when a
file's main value is one component.

## Rendering the app

An app's entry point commonly mounts a top-level component into a DOM element.
For example, with a `div` whose `id` is `"root"` in the HTML:

```jsx
import { createRoot } from "react-dom/client";
import App from "./App";

createRoot(document.getElementById("root")).render(<App />);
```

The flow is: export a component, import it where needed, include it in JSX,
then render the top-level component into the page. A framework or project
setup may provide this entry point and mounting step for you.

## See also

- [JSX basics](jsx.md) — JSX syntax.
- [Props](props.md) — component inputs and reusable APIs.
- [State with `useState`](use-state.md) — state that changes over time.
- [Back to React fundamentals](README.md)
