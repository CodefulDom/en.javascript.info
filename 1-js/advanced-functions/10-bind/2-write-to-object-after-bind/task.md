# task

importance: 5

## Bound function as a method

What will be the output?

```javascript
function f() {
  alert( this ); // ?
}

let user = {
  g: f.bind(null)
};

user.g();
```

