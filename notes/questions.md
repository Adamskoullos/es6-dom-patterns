- [Cloning](#Cloning)
- [HTML5](#HTML5)
- [CSS Calc](#CSS-Calc)
- [Media Queries](#Media-Queries)
- [CSS Selectors](#CSS-Selectors)
- [Class](#Class)
- [Event Loop](#Event-Loop)
- [Function vs Lambda](#Function-vs-Lambda)
- [Scoping and Hoisting](#Scoping-and-Hoisting)
- [This](#This)

---

### Cloning

1. Use `spreading` Immutable for shallow cloning
2. use `Object.Assign({}, item)` > But mutates nested data
3. Deep clone with `const newData = JSON.parse(JSON.stringify(data))` > does not clone `functions`

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

---

### Class

```js
class Cart {
  items;
  // Freeze on the way in
  constructor(items = []) {
    this.items = Object.freeze(items);
  }
  // Freeze on update
  add(item) {
    const state = [...this.items, item];
    this.items = Object.freeze(state);
  }
  remove(id) {
    const state = this.items.filter((item) => item.id !== id);
    this.items = Object.freeze(state);
  }
}
```

Setters and Getters:

```js
class Cart {
  // Properties
  #items;

  constructor(items = []) {
    this.value = items;
  }
  // Setter = freeze on the way in
  set value(items) {
    this.#items = Object.freeze(items);
  }

  // Getter = freeze on the way out
  get value() {
    return Object.freeze(this.#items);
  }
  // Methods
  add(item) {
    this.value = [...this.value, item];
  }
  remove(i) {
    this.value = this.value.filter((item) => item !== i);
  }
}
```

---

### Event Loop

---

### Function vs Lambda

---

### Scoping and Hoisting

- `Var` within a function has a function scope, otherwise it is available within the global scope
- `let` and `const` have block scope whe within the functions parenthesis

- Variables in parent scope are accessible in child scopes

- function `definitions` are hoisted, `expressions` are not

---

### Primitive vs Reference Data Types

- `Primitive` values are immutable and shared by copy
- `Reference` values are mutable and shared by reference

**Primitive Values**: (immutable non-object values)

- number
- string
- boolean
- symbol
- null
- undefined
- bigint

**Reference Values**: Objects, Arrays and Functions

**Solutions**:

1. Use `spreading` for shallow cloning
2. use `Object.Assign({}, item)` > But mutates nested data
3. Deep clone with `const newData = JSON.stringify(JSON.parse(data))` > does not clone `functions`

---

### Closure

Data accessible within a functions parent scope (closure scope) when defined which is also used within the function is accessible thereafter every time the function is invoked.

**Key Note**:

The data referenced within the function at the time the function is invoked references the current value of that data at the time of invocation.

---

### Recursion

Recursive functions need to have the bellow core pattern:

```js
function myFunc(n) {
  if (n === 0) return 1; // Base case to exit the cycle

  // Logic

  return myFunc(n - 1); // recursive step
}
```

---

### This

`This` refers to the current object/function it is being called on and not to the object/class it was defined in.

This allows dynamic values to be used for each new instance.

If `this` has no scope value when it is called it will refer to the global object

---
