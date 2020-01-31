# task

importance: 5

## Changing "prototype"

In the code below we create `new Rabbit`, and then try to modify its prototype.

In the start, we have this code:

\`\`\`js run function Rabbit\(\) {} Rabbit.prototype = { eats: true };

let rabbit = new Rabbit\(\);

alert\( rabbit.eats \); // true

```text
1. We added one more string (emphasized). What will `alert` show now?

    ```js
    function Rabbit() {}
    Rabbit.prototype = {
      eats: true
    };

    let rabbit = new Rabbit();

    *!*
    Rabbit.prototype = {};
    */!*

    alert( rabbit.eats ); // ?
```

1. ...And if the code is like this \(replaced one line\)?

   ```javascript
    function Rabbit() {}
    Rabbit.prototype = {
      eats: true
    };

    let rabbit = new Rabbit();

    *!*
    Rabbit.prototype.eats = false;
    */!*

    alert( rabbit.eats ); // ?
   ```

2. And like this \(replaced one line\)?

   ```javascript
    function Rabbit() {}
    Rabbit.prototype = {
      eats: true
    };

    let rabbit = new Rabbit();

    *!*
    delete rabbit.eats;
    */!*

    alert( rabbit.eats ); // ?
   ```

3. The last variant:

   ```javascript
    function Rabbit() {}
    Rabbit.prototype = {
      eats: true
    };

    let rabbit = new Rabbit();

    *!*
    delete Rabbit.prototype.eats;
    */!*

    alert( rabbit.eats ); // ?
   ```

