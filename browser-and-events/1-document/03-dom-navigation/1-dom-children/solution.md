# solution

There are many ways, for instance:

The `<div>` DOM node:

```javascript
document.body.firstElementChild
// or
document.body.children[0]
// or (the first node is space, so we take 2nd)
document.body.childNodes[1]
```

The `<ul>` DOM node:

```javascript
document.body.lastElementChild
// or
document.body.children[1]
```

The second `<li>` \(with Pete\):

```javascript
// get <ul>, and then get its last element child
document.body.lastElementChild.lastElementChild
```

