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
different data:

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

function App() {
  return (
    <>
      <Greeting name="Maya" />
      <Greeting name="Leo" />
    </>
  );
}
```

Treat props as read-only. Pass a callback prop when a child needs to ask its
parent to perform an action.

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

For JSX syntax details, see [JSX basics](jsx.md). For state that changes over
time, see [State with `useState`](use-state.md).
