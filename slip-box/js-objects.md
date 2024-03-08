# Object
In computer science, an object is a value in memory which is possibly referenced by an identifier. In JavaScript, objects are the only mutable values. Functions are, in fact, also objects with the additional capability of being callable.

## Object.hasOwn()
Ignore index if value is not defined for index (e.g. in sparse arrays).
```js
const arr = [1, , 3];

for(let i = 0; i < arr.length; i++) {
  console.log(`value: ${arr[i]}, index: ${i} and hasOwn: ${Object.hasOwn(arr, i)}`);
}

// value: 1, index: 0 and hasOwn: true
// value: undefined, index: 1 and hasOwn: false
// value: 3, index: 2 and hasOwn: true
```
