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

# Posting FormData via Fetch API
