# Querying DOM Nodes - HTMLCollections

When using `HTMLCollections` we only need to grab the elements(s) once as HTMLCollections are live, meaning when the property is used again it has the live current value:

```js
const data = ["Earth", "Fire", "Water"];
const fragment = document.createDocumentFragment();

data.forEach((item) => {
  const li = document.createElement("li");
  li.className = "list-item";
  li.innerText = item;
  fragment.append(li);
});

// getElementById: HTMLElement
const ulFromId = document.getElementById("list");
console.log(ulFromId);
ulFromId.append(fragment);

// getElementsByClassName: HTMLCollection
const listItemsFromClassName = ulFromId.getElementsByClassName("list-item");
console.log(listItemsFromClassName);

// getElementsByTagName: HTMLCollection
const listItemsFromTagName = ulFromId.getElementsByTagName("li");
console.log(listItemsFromTagName);

// Demonstrate live collection
const newListItem = document.createElement("li");
newListItem.className = "list-item";
newListItem.innerText = "Air";
ulFromId.append(newListItem);

// No need to query again!
console.log(listItemsFromClassName);
console.log(listItemsFromTagName);
```

# Querying DOM Nodes - NodeLists

`querySelector` and `querySelectorAll` returns an HTMLElement or any other node or **nodeList** rather than an HTMLCollection. This means that a new query needs to be made each time in order to grab the current value.

# Convert NodeList to Array

We can loop through a NodeList using a `for of` loop however to work with array methods we want to convert the NodeList into an actual array:

```js
const listItems = document.querySelectorAll("#list li");

[...listItems].forEach((item) => console.log(item));
```

# Finding Child Elements

**.children** is a really nice way to grab child elements:

```js
const list = document.querySelector("#list");
const selectedIndex = 2;

// querySelectorAll: NodeList - Returns element node
const queryChildren = list.querySelectorAll("li");
console.log(queryChildren[selectedIndex], queryChildren.length);

// .children: HTMLCollection - Returns element node
console.log(list.children[selectedIndex], list.children.length);

// .childNodes: NodeList - Do not use this as it returns every node and we want only element nodes
console.log(list.childNodes[selectedIndex], list.childNodes.length);

// first/last
console.log(list.firstElementChild);
console.log(list.lastElementChild);
```

# Grabbing Parent Element

**item.parentElement** grabs an elements parent. This can be chained to grab the parent of the parent and climb up the DOM tree

# Grabbing Sibling Elements

**nextElementSibling**
**previousElementSibling**

```js
// Any Element Nodes
console.log(listItem.nextElementSibling);
console.log(listItem.previousElementSibling);
```
