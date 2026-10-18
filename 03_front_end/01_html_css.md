# Front End — HTML & CSS

## HTML Skeleton

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header><nav>...</nav></header>
  <main>
    <article><h1>Heading</h1><p>Text</p></article>
  </main>
  <footer>...</footer>
  <script src="app.js" defer></script>
</body>
</html>
```

## Semantic Elements

`header` `nav` `main` `section` `article` `aside` `footer` — improve accessibility and SEO. Prefer over generic `div`.

## Forms

```html
<form action="/login" method="post">
  <label for="email">Email</label>
  <input type="email" id="email" name="email" required>
  <label for="pw">Password</label>
  <input type="password" id="pw" name="pw" minlength="8" required>
  <button type="submit">Log in</button>
</form>
```

- Every input needs a `label`.
- HTML validation is convenience only; server must validate again.

## CSS Selectors

| Selector | Example | Targets |
|----------|---------|---------|
| Element | `p` | all paragraphs |
| Class | `.card` | class="card" |
| ID | `#nav` | id="nav" (unique) |
| Descendant | `nav a` | links inside nav |
| Pseudo-class | `a:hover` | hovered links |

Specificity: inline > ID > class > element. Later rule wins ties.

## Box Model

Content → padding → border → margin.

```css
* { box-sizing: border-box; }  /* width includes padding + border */
```

## Flexbox (1-D layout)

```css
.row {
  display: flex;
  justify-content: space-between;  /* main axis */
  align-items: center;             /* cross axis */
  gap: 1rem;
  flex-wrap: wrap;
}
```

## Grid (2-D layout)

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
}
```

## Responsive Design

```css
.container { max-width: 960px; margin: 0 auto; padding: 0 1rem; }

@media (max-width: 600px) {
  .row { flex-direction: column; }
}
```

Mobile-first: base styles for small screens, `min-width` queries for larger.

## Units

`px` fixed · `rem` relative to root font · `em` relative to parent · `%` relative to parent · `vw/vh` viewport.

## CSS Variables

```css
:root { --primary: #2563eb; }
.btn { background: var(--primary); }
```

## Gotchas

- Margin collapsing between vertical sibling margins.
- `display: none` removes from layout; `visibility: hidden` keeps space.
- Missing viewport meta tag breaks mobile layout.
- Always include `alt` text on images.
