# Promise: then versus catch

Are these code fragments equal? In other words, do they behave the same way in any circumstances, for any handler functions?

```javascript
promise.then(f1).catch(f2);
```

Versus:

```javascript
promise.then(f1, f2);
```

