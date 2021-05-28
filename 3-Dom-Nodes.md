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
