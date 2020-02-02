# task

importance: 4

## Uppercase const?

Examine the following code:

```javascript
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Here we have a constant `birthday` date and the `age` is calculated from `birthday` with the help of some code \(it is not provided for shortness, and because details don't matter here\).

Would it be right to use upper case for `birthday`? For `age`? Or even for both?

```javascript
const BIRTHDAY = '18.04.1982'; // make uppercase?

const AGE = someCode(BIRTHDAY); // make uppercase?
```

