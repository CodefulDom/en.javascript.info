# solution

To add the button we can use either `position:absolute` \(and make the pane `position:relative`\) or `float:right`. The `float:right` has the benefit that the button never overlaps the text, but `position:absolute` gives more freedom. So the choice is yours.

Then for each pane the code can be like:

```javascript
pane.insertAdjacentHTML("afterbegin", '<button class="remove-button">[x]</button>');
```

Then the `<button>` becomes `pane.firstChild`, so we can add a handler to it like this:

```javascript
pane.firstChild.onclick = () => pane.remove();
```

