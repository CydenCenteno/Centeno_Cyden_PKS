# Front End — JavaScript & DOM

## Variables & Types

```js
const PI = 3.14;      // cannot reassign
let count = 0;        // can reassign, block-scoped
// avoid var (function-scoped, hoisted)
```

Types: string, number, boolean, null, undefined, object, array (object), symbol, bigint.

## Equality

- `===` strict (no coercion). Prefer always.
- `==` loose, coerces: `"5" == 5` is true.
- Falsy: `false 0 "" null undefined NaN`.

## Functions

```js
function add(a, b) { return a + b; }
const addArrow = (a, b) => a + b;
```

## Arrays — Useful Methods

```js
const nums = [1, 2, 3, 4];
nums.map(n => n * 2);          // [2,4,6,8]
nums.filter(n => n % 2 === 0); // [2,4]
nums.reduce((s, n) => s + n, 0); // 10
nums.find(n => n > 2);         // 3
```

## Objects & Destructuring

```js
const user = { name: "Ana", age: 20 };
const { name, age } = user;
const copy = { ...user, age: 21 };   // spread, immutable update
```

## DOM Manipulation

```js
const btn = document.querySelector("#save");
const list = document.querySelector(".items");

btn.addEventListener("click", () => {
  const li = document.createElement("li");
  li.textContent = "New item";     // safe (no HTML parsing)
  list.appendChild(li);
  list.classList.toggle("active");
});
```

Use `textContent`, not `innerHTML`, for user-provided data (prevents XSS).

## Events

`click` `input` `change` `submit` `keydown` `DOMContentLoaded`.

```js
form.addEventListener("submit", (e) => {
  e.preventDefault();   // stop page reload
});
```

## Async: Promises & fetch

```js
async function loadUsers() {
  try {
    const res = await fetch("/api/users");
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    const data = await res.json();
    return data;
  } catch (err) {
    console.error("Load failed:", err);
    return [];
  }
}
```

- `fetch` does **not** reject on 404/500 — check `res.ok`.
- `await` only inside `async` function (or module top level).

POST JSON:

```js
await fetch("/api/users", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Ana" })
});
```

## Storage

- `localStorage` — persists, strings only (`JSON.stringify/parse`).
- `sessionStorage` — cleared when tab closes.
- Never store tokens/secrets in localStorage if XSS is a risk.

## Gotchas

- Script before DOM loads → null elements. Use `defer`.
- `this` differs in arrow vs regular functions.
- Floating point: `0.1 + 0.2 !== 0.3`.
- Same-origin policy / CORS blocks cross-origin requests unless server allows.
