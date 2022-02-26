## Cheatsheet

- [HTML5](#HTML5)
- [CSS Calc](#CSS-Calc)
- [Media Queries](#Media-Queries)
- [CSS Selectors](#CSS-Selectors)

---

### HTML5

- article
- aside
- details
- figcaption
- figure
- footer
- header
- main
- mark
- nav
- section
- summary
- time

```html
<body>
  <nav></nav>
  <header></header>
  <main>
    <section></section>
  </main>
  <footer></footer>
</body>
```

---

### CSS Calc

```cs
width: calc(100% - 100px);
```

---

### Media Queries

```css
/* When the browser is at least 600px and above */
@media screen and (min-width: 600px) {
  .element {
    /* Apply some styles */
  }
}

/* Viewports between 320px and 480px wide */
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) {
  .element {
    /* Apply some styles */
  }
}
```

---

### CSS Selectors

Psuedo Elements:

```scss
//Creates empty element before children
.parent-element::before {
  content: "Before";
  // any other styling
}
//Creates empty element after children
.parent-element::after {
  content: "Before";
  // any other styling
}
```

Psuedo Classes (`state`):

```scss
.element:hover {
  // some styling
}
```
