## JavaScript Releases

### ES6 2015

- `let` and `const`
- `Arrow` functions
- `for of loop`:

```js
for (let x of cars) {
}
```

- Map & Set Objects
- `classes`

  - Private
  - Static
  - prototypes in class

- `Promises`:

```js
const myPromise = new Promise(function (myResolve, myReject) {
  myResolve(); // when successful
  myReject(); // when error
});

myPromise.then(
  function (value) {
    /* code if successful */
  },
  function (error) {
    /* code if some error */
  }
);
```

- `defaults` > myFunc(item = 'dafault'){}
- `Rest / Spread Operator`
- string.includes(), .startsWith(), . endsWith()
- JS Modules
- Array.from(), .keys(), .find()
- `{ data, loading, error }` > Destructuring
- `Template strings`

---

### ES7 2016

- array.includes('item')

### ES8 2017

- `Async` for function using `promises`

### ES9 2018

- `Await`
- `.finally()` added to `.then().catch().finally()`
- { ...obj }

### ES10 2019

- Array.flat() >
- Array.flatmap() >
- String.trimStart(), trimEnd()

### ES11 2020

- import()
- Nullish > `??`
- Optional Chaining > `?.`

### ES12 2021

- replaceAll > `string.replaceAll('old', 'new')`
- Numeric separator: `1_000_000_000`
- Private methods (classes) > `#privateMethod()`

- Promise.any() >

```js
const first = new Promise((resolve, reject) => {
  reject("I am rejected");
});

const second = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, "I will resolve in 500ms");
});

const third = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "I will resolve in 100ms");
});

Promise.any([first, second, third]).then((response) => {
  console.log(response);
});

// Output: I will resolve in 100ms
```
