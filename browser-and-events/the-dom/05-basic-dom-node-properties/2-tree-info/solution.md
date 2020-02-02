# solution

Let's make a loop over `<li>`:

```javascript
for (let li of document.querySelectorAll('li')) {
  ...
}
```

In the loop we need to get the text inside every `li`.

We can read the text from the first child node of `li`, that is the text node:

```javascript
for (let li of document.querySelectorAll('li')) {
  let title = li.firstChild.data;

  // title is the text in <li> before any other nodes
}
```

Then we can get the number of descendants as `li.getElementsByTagName('li').length`.

