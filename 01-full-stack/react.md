# React

## Docs:

[https://react.dev/learn](https://react.dev/learn)



## Vite

```
pnpm create vite
```

```
pnpm run dev
```

```
pnpm i react-router-dom
```









## React vs HTML

When copying plain HTML into React, several things can “break” because React uses JSX, which looks like HTML but follows JavaScript rules underneath.

Here are the main incompatibilities and gotchas:

### 1. `class` → `className`

HTML:

```html
<div class="box"></div>
```

React:

```jsx
<div className="box"></div>
```

Why:\
`class` is a reserved JavaScript keyword.

***

## 2. `for` → `htmlFor`

HTML:

```html
<label for="email">Email</label>
```

React:

```jsx
<label htmlFor="email">Email</label>
```

Why:\
`for` is reserved in JavaScript.

***

## . Inline styles use objects, not strings

HTML:

```html
<div style="color:red; font-size:20px"></div>
```

React:

```jsx
<div style={{ color: 'red', fontSize: '20px' }}></div>
```

Differences:

* object instead of string
* camelCase properties
* values often strings

***

## . Attribute names become camelCase

HTML:

```html
<div tabindex="0"></div>
```

React:

```jsx
<div tabIndex={0}></div>
```

Examples:

| HTML      | React     |
| --------- | --------- |
| tabindex  | tabIndex  |
| maxlength | maxLength |
| readonly  | readOnly  |
| colspan   | colSpan   |

***

***

## . Some HTML attributes are reserved or renamed

Examples:

| HTML     | React    |
| -------- | -------- |
| onclick  | onClick  |
| onchange | onChange |
| onsubmit | onSubmit |

Event names are camelCase.

***

## 10. Events use functions, not strings

HTML:

```html
<button onclick="alert('hi')">
```

React:

```jsx
<button onClick={() => alert('hi')}>
```

No inline JavaScript strings.

***

## 11. `selected` and `checked` behave differently

HTML:

```html
<option selected>
```

React:

```jsx
<select value="x">
```

and:

```jsx
<input checked={true} />
```

React prefers controlled state.

***

## 13. SVG attributes differ

HTML/SVG:

```html
<svg stroke-width="2">
```

React:

```jsx
<svg strokeWidth="2">
```

Most SVG props become camelCase too.

***

## 14. Boolean attributes behave differently

HTML:

```html
<input disabled>
```

React:

```jsx
<input disabled={true} />
```

***

## 15. `script` tags usually don’t execute

Pasted HTML with:

```html
<script>alert(1)</script>
```

inside JSX typically will not run the way normal HTML does.

***

***

## 19. Custom attributes may get stripped or warned

Older React versions removed unknown attributes.

Modern React mostly allows:

```jsx
data-id=""
aria-label=""
```

But random attributes may still warn.

***

## 20. Copy-pasted HTML often includes invalid nesting

Browsers autocorrect invalid HTML:

```html
<p><div>x</div></p>
```

React is stricter and warns/errors.

***

## 21. JSX is not real HTML

This is the biggest issue.

JSX compiles into:

```js
React.createElement(...)
```

So even though it _looks_ like HTML, it follows JavaScript syntax rules.

***

***

## 28. React escapes HTML by default

This prevents XSS:

```jsx
<div>{userInput}</div>
```

HTML is escaped automatically.

Plain HTML expectations often fail because of this safety feature.

***

## 29. Attribute value types change

HTML:

```html
<input maxlength="5">
```

React:

```jsx
<input maxLength={5}>
```

Numbers/booleans become JavaScript values.

***

## &#x20;All tags must be closed

HTML allows:

```html
<br>
```

React requires:

```jsx
<br />
```

## &#x20;Multiple root elements are not allowed

HTML:

```html
<h1>Hello</h1>
<p>World</p>
```

React component must wrap:

```jsx
<>
  <h1>Hello</h1>
  <p>World</p>
</>
```

or:

```jsx
<div>
  ...
</div>
```

## . JavaScript expressions need `{}`

HTML:

```html
<h1>username</h1>
```

React dynamic:

```jsx
<h1>{username}</h1>
```

Without `{}`, React treats it as plain text.
