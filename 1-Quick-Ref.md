# Traversing Elements

- parentElement
- children
- children[0]
- firstElementChild
- lastElementChild
- nextElementSibling
- previousElementSibling

# Modify Element

```js
node.style.color = "red";

node.style.padding = "10px";

node.setAttribute("attr-name", "attr-value");

node.removeAttribute("attr-name");
```

# Modify Element Class

```js
node.classList.add("class-name");

node.classList.remove("class-name");

node.classList.toggle("class-name");

node.classList.contains("class-name");

node.classList.replace("old", "new");
```

# Remove Node

```js
parentNod.removeChild("nodeToRemove");

// Hack to remove self
nodeToRemove.parentNode.removeChild("nodeToRemove");
```
