# JSX basics

JSX is JavaScript syntax for describing React UI. It looks like HTML, but it
is not an HTML string: JSX expressions are transformed into JavaScript that
describes the elements React should render.

```jsx
const heading = <h1>Hello, world!</h1>;
```

Use `{}` to put a JavaScript expression in JSX. For example:

```jsx
<h1>Hello, {name}!</h1>
{isReady ? <Content /> : <Spinner />}
```

Braces accept expressions that produce values, not statements such as `if` or
`for`. Use a ternary or `&&` for common conditional rendering.

A component's returned JSX needs one outermost element. A Fragment
(`<>...</>`) groups elements without adding a DOM element:

```jsx
function Welcome() {
  return (
    <>
      <h1>Welcome</h1>
      <p>Glad you're here.</p>
    </>
  );
}
```

JSX attributes mostly resemble HTML, but use names such as `className` and
`htmlFor`; event handlers use camelCase, such as `onClick`.

When rendering a list with `.map()`, give each item a stable `key` so React
can match items between renders. A stable ID is generally preferable to an
array index, especially when items can be reordered, added, or removed.

## See also

- [Function components](components.md) — defining and composing components
  with JSX.
- [Back to React fundamentals](README.md)
