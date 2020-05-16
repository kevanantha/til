# What Is The Use Of The Javascript `bind`?

- Bind creates a new function that will force the `this` inside the function to be the parameter passed to `bind()`
- The bind() method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

## Example

```javascript
const button = {
  content: 'ok',
  click() {
    console.log(`${this.content} bro`)
  },
}

button.click() // ok bro

const myButton = button.click
myButton() // undefined bro, The function gets invoked at the global scope or global `this`

const myBindButton = button.click.bind(button)
myBindButton() // ok bro
```

Another examples from MDN

```javascript
function list() {
  return Array.prototype.slice.call(arguments)
}

function addArguments(arg1, arg2) {
  return arg1 + arg2
}

const list1 = list(1, 2, 3)
//  [1, 2, 3]

const result1 = addArguments(1, 2)
//  3

// Create a function with a preset leading argument
const leadingThirtysevenList = list.bind(null, 37)

// Create a function with a preset first argument.
const addThirtySeven = addArguments.bind(null, 37)

const list2 = leadingThirtysevenList()
//  [37]

const list3 = leadingThirtysevenList(1, 2, 3)
//  [37, 1, 2, 3]

const result2 = addThirtySeven(5)
//  37 + 5 = 42

const result3 = addThirtySeven(5, 10)
//  37 + 5 = 42
//  (the second argument is ignored)
```

---

## Refs

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
- [Stackoverflow](https://stackoverflow.com/questions/2236747/what-is-the-use-of-the-javascript-bind-method)
- [Javascripture](https://www.javascripture.com/Function#bind)

## Tags

- #javascript
- #bind
