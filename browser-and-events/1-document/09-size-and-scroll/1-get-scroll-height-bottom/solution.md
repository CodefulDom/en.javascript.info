# solution

The solution is:

```javascript
let scrollBottom = elem.scrollHeight - elem.scrollTop - elem.clientHeight;
```

In other words: \(full height\) minus \(scrolled out top part\) minus \(visible part\) -- that's exactly the scrolled out bottom part.

