# task

importance: 3

## Make external links orange

Make all external links orange by altering their `style` property.

A link is external if:

* Its `href` has `://` in it
* But doesn't start with `http://internal.com`.

Example:

\`\`\`html run [the list](task.md)

* [http://google.com](http://google.com)
* [/tutorial.html](https://github.com/CodefulDom/en.javascript.info/tree/a035351fcfceb747760a1d9bd2c652f624999a4a/tutorial/README.md)
* [local/path](https://github.com/CodefulDom/en.javascript.info/tree/a035351fcfceb747760a1d9bd2c652f624999a4a/2-ui/1-document/06-dom-attributes-and-properties/2-yellow-links/local/path/README.md)
* [ftp://ftp.com/my.zip](ftp://ftp.com/my.zip)
* [http://nodejs.org](http://nodejs.org)
* [http://internal.com/test](http://internal.com/test)

 // setting style for a single link let link = document.querySelector\(&apos;a&apos;\); link.style.color = &apos;orange&apos;; 

\`\`\`

The result should be:

\[iframe border=1 height=180 src="solution"\]

