# task

importance: 1

## Why does "aaa" remain?

In the example below, the call `table.remove()` removes the table from the document.

But if you run it, you can see that the text `"aaa"` is still visible.

Why does that happen?

\`\`\`html height=100 run

|  aaa |
| :--- |
| Test |

 alert\(table\); // the table, as it should be

table.remove\(\); // why there's still aaa in the document? &lt;/script&gt;

\`\`\`

