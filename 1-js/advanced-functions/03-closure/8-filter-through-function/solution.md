# Filter inBetween

\`\`\`js run function inBetween\(a, b\) { return function\(x\) { return x &gt;= a && x &lt;= b; }; }

let arr = \[1, 2, 3, 4, 5, 6, 7\]; alert\( arr.filter\(inBetween\(3, 6\)\) \); // 3,4,5,6

```text
# Filter inArray

```js run demo
function inArray(arr) {
  return function(x) {
    return arr.includes(x);
  };
}

let arr = [1, 2, 3, 4, 5, 6, 7];
alert( arr.filter(inArray([1, 2, 10])) ); // 1,2
```

