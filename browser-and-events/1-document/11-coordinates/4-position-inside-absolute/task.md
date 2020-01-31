# task

importance: 5

## Position the note inside \(absolute\)

Extend the previous task &lt;info:task/position-at-absolute&gt;: teach the function `positionAt(anchor, position, elem)` to insert `elem` inside the `anchor`.

New values for `position`:

* `top-out`, `right-out`, `bottom-out` -- work the same as before, they insert the `elem` over/right/under `anchor`.
* `top-in`, `right-in`, `bottom-in` -- insert `elem` inside the `anchor`: stick it to the upper/right/bottom edge.

For instance:

```javascript
// shows the note above blockquote
positionAt(blockquote, "top-out", note);

// shows the note inside blockquote, at the top
positionAt(blockquote, "top-in", note);
```

The result:

\[iframe src="solution" height="310" border="1" link\]

As the source code, take the solution of the task &lt;info:task/position-at-absolute&gt;.

