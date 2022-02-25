## Questions

**`Event Loop`**

---

**`Scoping and Hoisting`**

- `Var` within a function has a function scope, otherwise it is available within the global scope
- `let` and `const` have block scope whe within the functions parenthesis

- Variables in parent scope are accessible in child scopes

- function `definitions` are hoisted, `expressions` are not

---

**`Primitive vs Reference Data Types`**

- `Primitive` values are immutable and shared by copy
- `Reference` values are mutable and shared by reference

**Primitive Values**: (immutable non-object values)

- number
- string
- boolean
- symbol
- null
- undefined
- bigint

**Reference Values**: Objects, Arrays and Functions

**Solutions**:

1. Use `spreading` for shallow cloning
2. use `Object.Assign({}, item)` > But mutates nested data
3. Deep clone with `const newData = JSON.stringify(JSON.parse(data))` > does not clone `functions`

---

**`Closure`**

Data accessible within a functions parent scope (closure scope) when defined which is also used within the function is accessible thereafter every time the function is invoked.

**Key Note**:

The data referenced within the function at the time the function is invoked references the current value of that data at the time of invocation.

---

**`Recursion`**

Recursive functions need to have the bellow core pattern:

```js
function myFunc(n) {
  if (n === 0) return 1; // Base case to exit the cycle

  // Logic

  return myFunc(n - 1); // recursive step
}
```
