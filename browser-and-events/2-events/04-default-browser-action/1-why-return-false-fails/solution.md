# solution

When the browser reads the `on*` attribute like `onclick`, it creates the handler from its content.

For `onclick="handler()"` the function will be:

```javascript
function(event) {
  handler() // the content of onclick
}
```

Now we can see that the value returned by `handler()` is not used and does not affect the result.

The fix is simple:

\`\`\`html run

  
  function handler\(\) {  
    alert\("..."\);  
    return false;  
  }  


[w3.org](https://w3.org)

```text
Also we can use `event.preventDefault()`, like this:

```html run
<script>
*!*
  function handler(event) {
    alert("...");
    event.preventDefault();
  }
*/!*
</script>

<a href="https://w3.org" onclick="*!*handler(event)*/!*">w3.org</a>
```

