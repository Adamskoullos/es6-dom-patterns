## css Grid

- [Full example](#Grid-Templates)

---

- The below example has a `grid` container set to `display: grid`
- `grid-template-columns: 1fr 1fr 1fr;` spreads the content evenly across 3 columns
- `grid-auto-rows: minmax(1fr, auto);` gives each row a min height of `1fr` but allows a row to increase to the height required by the tallest section
- `gap: 10px;` gives an even gap around each section

```scss
#dojo-section {
  height: 80vh;
  overflow: auto;
  padding: 10px;

  .grid {
    height: 100%;
    display: grid;
    // grid-template-columns: repeat(3, 1fr);
    grid-template-columns: 1fr 1fr 1fr;

    // Manage min and max height of rows
    grid-auto-rows: minmax(1fr, auto);

    // The above is good when unknown number of rows
    // grid-template-rows: repeat(3, minmax(1fr, auto));
    // grid-template-rows: 1fr 1fr 1fr;

    gap: 10px;
    // row-gap: 20px;
    // column-gap: 40px;

    div {
      text-align: center;
      background: #3bbced;
      padding: 15px;
      &:nth-child(even) {
        background: #777;
      }
    }
  }
}
```

![Screenshot from 2022-02-26 07-52-30](https://user-images.githubusercontent.com/73107656/155835160-d36ea525-9fd3-41a5-86a3-7197fa5a7e6b.png)

---

## Positioning Grid Items

```html
<div class="grid">
  <div class="one">1</div>
  <div class="two">2</div>
  <div class="three">3</div>
  <div class="four">4</div>
  <div class="five">5</div>
  <div class="six">6</div>
</div>
```

1. Define the grid:

The example creates a grid with `6 columns` and `4 rows`:

```scss
.grid {
  height: 100%;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(4, minmax(1fr, auto));
  gap: 10px;
}
```

2. Position items within the grid:

The long-hand is commented out leaving the short-hand option.

```scss
.one {
  grid-column: 1/3;
}
.two {
  grid-column: 3/7;
}
.three {
  grid-column: 1/5;
  grid-row: 2/4;
}
.four {
  grid-column: 5/7;
  grid-row: 2/3;
}
.five {
  grid-column: 5/7;
  grid-row: 3/4;
}
.six {
  grid-column: 1/7;
}
```

![Screenshot from 2022-02-26 08-38-38](https://user-images.githubusercontent.com/73107656/155836509-d60b4c5f-f911-451f-958c-024bab4b6e3d.png)

## Nested Grids

```html
<section id="dojo-section">
  <div class="grid">
    <div class="one">1</div>
    <div class="two">2</div>
    <div class="three nested-grid">
      <div>A</div>
      <div>B</div>
      <div>C</div>
      <div>D</div>
    </div>
    <div class="four">4</div>
    <div class="five">5</div>
    <div class="six">6</div>
  </div>
</section>
```

```scss
#dojo-section {
  height: 80vh;
  overflow: auto;
  padding: 10px;

  .grid {
    height: 100%;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: repeat(4, minmax(1fr, auto));
    gap: 10px;

    div {
      text-align: center;
      background: #3bbced;
      padding: 15px;
      &:nth-child(even) {
        background: rgba(119, 119, 119, 0.76);
      }
    }

    .one {
      grid-column: 1/3;
    }
    .two {
      grid-column: 3/7;
    }
    .three {
      grid-column: 1/5;
      grid-row: 2/6;
      &.nested-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-template-rows: repeat(2, minmax(1fr, auto));
        gap: 10px;
        div {
          background: #9ceea0e1;
        }
      }
    }
    .four {
      grid-column: 5/7;
      grid-row: 2/6;
    }
    .five {
      grid-column: 6/7;
      grid-row: 6/7;
    }
    .six {
      grid-column: 1/6;
    }
  }
}
```

![Screenshot from 2022-02-26 08-55-18](https://user-images.githubusercontent.com/73107656/155836995-73e37153-9f74-42fa-9de5-edad21edc2cd.png)

---

## Grid Templates

```html
<div class="grid-container">
  <header>Header</header>
  <main>
    Main
    <section>
      <div>One</div>
      <div>Two</div>
      <div>Three</div>
    </section>
  </main>
  <aside>Aside</aside>
  <footer>Footer</footer>
</div>
```

```scss
.grid-container {
  height: 80vh;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 5px;
  grid-template-areas:
    "main main main main aside aside"
    "main main main main aside aside"
    "main main main main aside aside"
    "main main main main aside aside"
    "main main main main aside aside"
    "main main main main aside aside";
  & > * {
    // background: rgb(138, 209, 117);
    padding: 20px;
  }
  main {
    grid-area: main;
    overflow: auto;
    section {
      height: 100%;
      display: grid;
      grid-template-columns: repeat(1, 1fr);
      grid-auto-rows: minmax(300px, auto);
      gap: 20px;
      div {
        background: rgba(100, 148, 237, 0.418);
        padding: 20px;
        box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.3);
        border-radius: 8px;
        transition: all 0.3s;
        &:hover {
          background: rgba(100, 148, 237, 0.527);
          transform: scale(1.005);
          box-shadow: 1px 3px 4px rgba(0, 0, 0, 0.4);
          transition: all 0.3s;
        }
      }
    }
  }
  aside {
    grid-area: aside;
  }
}
```

![Screenshot from 2022-02-26 11-00-22](https://user-images.githubusercontent.com/73107656/155840720-0f7e2f16-b5ff-4aeb-beb2-b34383948074.png)
