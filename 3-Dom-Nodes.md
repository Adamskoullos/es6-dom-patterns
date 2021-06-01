# Basic Node Hierarchy

- **EventTarget**
  - **Node**
    - **Element**
      - **HTMLElement**
        - **HTMLBodyElement**

# Node Types

1. **Element**
2. Attribute
3. Text
4. CDataSection
5. EntityReference
6. Entity
7. ProcessingInstruction
8. Comment
9. **Document**
10. DocumentType
11. DocumentFragment
12. Notation

# innerText vs textContent

innerText gives us just the text (Elements) where as textContent includes all nodes, including whitespace => Better to use **innertext**

# innerHTML vs createElement

```js
// Using document.createElement()
function createInputDOM({ label, type = "text" }) {
  const labelEl = document.createElement("label");
  const inputEl = document.createElement("input");

  inputEl.type = type;
  labelEl.innerText = label;
  labelEl.append(inputEl);

  return labelEl;
}

// Using string templates
function createInputTemplate({ label, type = "text" }) {
  return `
  <label>
    ${label}
    <input type="${type}">
  </label>
  `;
}

const inputFromTemplate = createInputTemplate({
  label: "Email",
  type: "email",
});
app.innerHTML += inputFromTemplate;
```

# DocumentFragment

In the process of looping through an array and rendering each item to the dom we can utilise `DocumentFragment` to batch render all items once rather than one item on each iteration. This is a more efficient technique when working with large data sets.

The below example appends each item to the fragment first and then once the loop is finished the fragment is rendered to the DOM once:

```js
const data = ["Earth", "Fire", "Water", "Air"];

const fragment = document.createDocumentFragment();

data.forEach((name) => {
  const li = document.createElement("li");
  li.innerText = name;
  fragment.append(li);
});

app.append(fragment);
```

# Inserting DOM Elements

```js
// Adds the span to the end of any elements within the div
div.append(span);

// Adds p to the start of any elements within the div
div.prepend(p);

// Adds i before p
p.before(i);

// Adds i after p
p.after(i);
```

# insertAdjacentHTML

Using string templates to surgically inject HTML into the DOM.

`insertAdjacentHTML` has two arguments, the first argument is **where** the string template is to be injected and the second argument is the string template to be injected.

The first argument has the below options:

```js
// Injects p before ul
ul.insertAdjacentHTML("beforebegin", "<p>Before</p>");

//  Injects li just inside ul as the first child
ul.insertAdjacentHTML("afterbegin", "<li>First</li>");

// Injects li as the last child within the ul
ul.insertAdjacentHTML("beforeend", "<li>Last</li>");

// Injects p just after the closing ul tag
ul.insertAdjacentHTML("afterend", "<p>After</p>");
```

# Replacing DOM Elements

For times when we do not want to just replace the content within an element we can replace one element for another using **replaceWith()**:

```js
const div = app.querySelector("div");

const newDiv = document.createElement("div");
newDiv.innerText = "I have been replaced!";

// new way
div.replaceWith(newDiv);

// old way
const anotherDiv = document.createElement("div");
anotherDiv.innerText = "I replace all";

setTimeout(() => {
  newDiv.parentNode.replaceChild(anotherDiv, newDiv);
}, 2000);
```

# Cloning DOM Elements

To copy a chunk of the DOM tree including nested elements we use `cloneNode(true)`:

```js
// cloneNode(true) clones all elements and subtrees
const newClone = div.cloneNode(true);
```

# Removing DOM Elements

```js
// New way
div.remove();

// Old way
div.parentNode.removeChild(div);
```
