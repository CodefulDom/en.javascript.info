# Find HTML comments

Find all HTML comments in the text:

```javascript
let regexp = /your regexp/g;

let str = `... <!-- My -- comment
 test --> ..  <!----> .. 
`;

alert( str.match(regexp) ); // '<!-- My -- comment \n test -->', '<!---->'
```

