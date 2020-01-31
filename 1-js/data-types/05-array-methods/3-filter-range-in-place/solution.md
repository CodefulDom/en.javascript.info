# solution

\`\`\`js run demo function filterRangeInPlace\(arr, a, b\) {

for \(let i = 0; i &lt; arr.length; i++\) { let val = arr\[i\];

```text
// remove if outside of the interval
if (val < a || val > b) {
  arr.splice(i, 1);
  i--;
}
```

}

}

let arr = \[5, 3, 8, 1\];

filterRangeInPlace\(arr, 1, 4\); // removed the numbers except from 1 to 4

alert\( arr \); // \[3, 1\]

\`\`\`

