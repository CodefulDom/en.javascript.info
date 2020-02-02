# solution

1. Either use a wrapper function, an arrow to be concise:

   ```javascript
    askPassword(() => user.login(true), () => user.login(false));
   ```

   Now it gets `user` from outer variables and runs it the normal way.

2. Or create a partial function from `user.login` that uses `user` as the context and has the correct first argument:

```javascript
    askPassword(user.login.bind(user, true), user.login.bind(user, false));
```

