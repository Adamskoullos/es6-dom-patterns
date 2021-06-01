# Setting & Getting HTML Attributes

```js
const button = document.querySelector("button");

// SET - Attribute name, Attribute value
button.setAttribute("aria-label", "Close this Modal");

// GET
const value = button.getAttribute("aria-label");
console.log(value);
```

# Setting and Getting Inline Styles

```js
// <button style="padding: 25px; margin: 10px 0;">
const button = document.querySelector("button");

// cssText
button.style.cssText = "padding: 25px; margin: 10px 0; font-size: 20px;";

// direct property access
button.style.fontSize = "22px";
button.style.marginTop = "15px";

console.log(button.style.fontSize); // provides the value
```

# Setting and Getting Classes

```js
const button = document.querySelector("button");

// Old way: Set
button.className += " three";

// Old way: Get
console.log(button.className.split(" "));

// New way: ClassList
// Add
button.classList.add("four");

// Remove
button.classList.remove("one");

// Toggle
button.classList.toggle("five");
setTimeout(() => button.classList.toggle("five"), 2500);

// Replace
button.classList.replace("two", "six");
```
