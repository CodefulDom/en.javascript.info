# solution

The answer: **`BODY`**.

\`\`\`html run

 let body = document.body;

body.innerHTML = "";

alert\( body.firstChild.data \); // BODY &lt;/script&gt;

\`\`\`

What's going on step by step:

1. The content of `<body>` is replaced with the comment. The comment is `<!--BODY-->`, because `body.tagName == "BODY"`. As we remember, `tagName` is always uppercase in HTML.
2. The comment is now the only child node, so we get it in `body.firstChild`.
3. The `data` property of the comment is its contents \(inside `<!--...-->`\): `"BODY"`.

