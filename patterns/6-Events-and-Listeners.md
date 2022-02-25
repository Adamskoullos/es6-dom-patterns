# Adding Event Listeners and Event Object

Pass in the `event` to capture the element:

```js
function handleClick(event) {
  console.log(event.target);
}

button.addEventListener("click", handleClick);

// arrow functions
button.addEventListener("dblclick", (event) => {
  console.log(event.target);
});
```

# Removing Event Listeners

```js
const button = document.querySelector("button");

// Define the callback
function handleClickOnce(event) {
  console.log(event.target);
  button.removeEventListener("click", handleClickOnce); // Removes listener after first click
}

// add listeners passing in the callback
button.addEventListener("click", handleClickOnce);

// Another way to remove after first click by using the third argument -------

button.addEventListener(
  "dblclick",
  () => {
    console.log("Double-click!");
  },
  { once: true }
);
```

# Event Bubbling, Capturing and Propagation

When an event is triggered the **capturing** phase begins at the top of the DOM tree (document.HTML) and trickles down through each element to the `event.target` where the event bounces and begins to **bubble** back up the DOM tree. This is called **propagation**.

This handy to understand as one event listener can be used to listen to a click from any one of a list of elements. By passing in the event we can access the event.target.

Note below how `event.stopPropagation()` is used to stop the event bubbling up the DOM tree any further:

```js
const one = document.querySelector(".one");
const two = document.querySelector(".two");
const three = document.querySelector(".three");

function handleClick(event) {
  event.stopPropagation();
  // event.stopImmediatePropagation();
  console.log(event.target);
}

one.addEventListener("click", handleClick);
two.addEventListener("click", handleClick);
three.addEventListener("click", handleClick);

three.addEventListener("click", (event) => console.log(event), {
  capture: true,
});
```

# Preventing Default Event Actions

The `event.preventDefault()` pattern prevents a page reload on form submission and can also be used as in the example below preventing the form from being submitted if it is not fully filled out:

```js
<form>
    <label>
        Sign-up Email
        <input type="email">
    </label>
    <label>
        I agree to the terms
        <input type="checkbox">
    </label>
</form>
;
```

```js
const form = document.querySelector("form");
const email = form.querySelector('input[type="email"]');
const checkbox = form.querySelector('input[type="checkbox"]');

function handleSubmit(event) {
  if (!checkbox.checked) {
    event.preventDefault();
    console.log("I am not submitting...");
    console.log(event.defaultPrevented);
    return;
  }
  console.log("Submitted", email.value);
}

form.addEventListener("submit", handleSubmit);
```

# Event Delegation and Dynamic Events

Example of adding the event listener to the parent element instead of each individual li tag:

```js
 <button type="button">
    Add Item
  </button>
 <ul id="list">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
  </ul>
;

const button = document.querySelector('button');
const list = document.querySelector('#list');

function handleClick(event) {
    // If the user clicks anywhere other than an li tag just return
  if (event.target.nodeName.toLowerCase() !== 'li') {
    return;
  }
//   Otherwise run the code
  console.log(event.target.innerText);
}
// Add single event listener to ul
list.addEventListener('click', handleClick);

button.addEventListener('click', () => {
  const items = list.querySelectorAll('li');
  const li = document.createElement('li');
  li.innerText = `Item ${items.length + 1}`;
  list.append(li);
});

```

# Keyboard Events

```js
document.addEventListener("keydown", (event) => {
  // console.log(event.key, event.code);
  switch (event.key) {
    case "ArrowUp": {
      console.log("Up!");
      event.preventDefault();
      break;
    }
    case "ArrowDown": {
      console.log("Down!");
      event.preventDefault();
      break;
    }
  }
});

document.addEventListener("keyup", (event) => console.log(event.key));
document.addEventListener("keydown", (event) => console.log(event.key));
```
