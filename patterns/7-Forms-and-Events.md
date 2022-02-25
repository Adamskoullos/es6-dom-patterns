# Accessing Forms and Elements

Note: The form below uses the **name** property for both the form and input elements. This makes it easy to grab the elements using the syntax below the form:

```js
<form name="order">
    <label>
      Your name
      <input type="text" name="fullname">
    </label>
  </form>
;
```

```js
// Grab form: document.forms.formName
const form = document.forms.order;

// Grab input: form.elements.elementName
const fullname = form.elements.fullname;

function handleInput(event) {
  // access the value
  console.log(event.target.value);

  // access the form
  console.log(event.target.form);
}

fullname.addEventListener("input", handleInput);
```

# Form Submit Event and FormData

```js
<form name="order">
    <label>
      Your name
      <input type="text" name="fullname">
    </label>
    <label>
      Which pizza would you like?
      <select name="pizza">
        <option value="pepperoni">Pepperoni</option>
        <option value="meaty">Meaty</option>
        <option value="cheesey">Cheesey</option>
      </select>
    </label>
    <button type="submit">
      Submit
    </button>
  </form>
;
```

```js
const form = document.forms.order;

function handleSubmit(event) {
  event.preventDefault();
  console.log(new FormData(event.target));
}

function handleFormData(event) {
  console.log(Array.from(event.formData));
  console.log(Array.from(event.formData.values()));
  const entries = event.formData.entries();
  for (const entry of entries) {
    console.log(entry);
  }
}

form.addEventListener("submit", handleSubmit);
form.addEventListener("formdata", handleFormData);
```

# Transforming FormData for the Server

Below shows the pattern to take form data and turn it into JSON ready to POST/PATCH.
This process takes advantage of the `FormData` constructor and also utilises the `JSON.stringify(Object.fromEntries(formData))` pattern which creates an object from the fromData and then stringifies it into JSON:

```js
<form name="order">
    <label>
      Your name
      <input type="text" name="fullname">
    </label>
    <label>
      Which pizza would you like?
      <select name="pizza">
        <option value="pepperoni">Pepperoni</option>
        <option value="meaty">Meaty</option>
        <option value="cheesey">Cheesey</option>
      </select>
    </label>
    <div>
      What size?
      <label>
        Small
        <input type="radio" name="size" value="small" checked>
      </label>
      <label>
        Medium
        <input type="radio" name="size" value="medium">
      </label>
      <label>
        Large
        <input type="radio" name="size" value="large">
      </label>
    </div>
    <label>
      Quantity
      <input type="number" name="quantity" value="1">
    </label>
    <button type="submit">
      Submit
    </button>
  </form>

```

```js
const form = document.forms.order;

function handleSubmit(event) {
  event.preventDefault();
  const formData = new FormData(event.target);

  // json
  const asJSON = JSON.stringify(Object.fromEntries(formData));
  console.log(asJSON);
}

form.addEventListener("submit", handleSubmit);
```

# Handling Input Elements

```js

<form name="example">
  <input type="text" name="myInput" value="Hello">
</form>
;
```

```js
const form = document.forms.example; // Grab form
const input = form.elements.myInput; // Grab input

// 1. Properties that are useful -----------------
console.dir(input);
// set
input.value = "Goodbye";
// input.readOnly = true;
// input.disabled = true;

// get
console.log(input.value);

// 2. Events
// other events: cut, copy and paste
input.addEventListener("focus", () => console.log("Focus"));
input.addEventListener("blur", () => console.log("Blur"));
input.addEventListener("input", () => console.log("Input"));
input.addEventListener("change", () => console.log("Change"));

// 3. Methods
// focus an input
input.focus();
setTimeout(() => input.blur(), 2500);
```

# Handling Radio Input Elements

```js
<form name="example">
    <div class="container">
      <label>
        Blue
        <input type="radio" name="color" value="blue">
      </label>
      <label>
        Red
        <input type="radio" name="color" value="red" checked>
      </label>
      <label>
        Green
        <input type="radio" name="color" value="green">
      </label>
    </div>
  </form>
;
```

```js
const form = document.forms.example;
const radios = Array.from(form.elements.color); // Grab all radios and save to array

// 1. Properties that are useful
radios[2].checked = true;
radios.forEach((radio) => {
  console.log(radio.value);
  console.log(radio.checked);
});

// 2. Events
const container = form.querySelector(".container");

container.addEventListener("change", () => {
  // const checked = radios.find(radio => radio.checked).value;
  // console.log(checked);
  console.log(form.elements.color.value);
});

// 3. Methods
radios[2].select();
```

# Handling Checkbox Input Elements

```html
<form name="example">
  <label>
    Marketing
    <input type="checkbox" name="marketing" />
  </label>
</form>
```

```js
const form = document.forms.example;
const checkbox = from.elements.marketing;

// Properties that are useful
console.dir(checkbox);

// Set
checkbox.checked = true;

// Events - Mostly use `change`
checkbox.addEventListener("change", () => {});

// Methods
checkbox.select();
```

# Handling Select Elements

```html
<form name="example">
  <select name="drink">
    <option value="">Select you drink</option>
    <option value="lemonade">Lemonade</option>
    <option value="cola">Cola</option>
    <option value="water">Water</option>
  </select>
</form>
```

```js
const form = document.forms.example;
const select = form.elements.drink;

// 1. Grab/see the value of the selected item
console.log(select.value);

// 2. Set
select.value = "water";

// 3. Selected index
console.log(select.selectedIndex);

// 4. Selected DOM Element
console.log(select.options[select.selectedIndex]);

// 5. Events - change

// 6. Add new <option>
const option = document.createElement("option");
option.value = "milk";
option.text = "Milk";

select.add(option, 1); // The 2nd argument being the index to inject the new element
```
