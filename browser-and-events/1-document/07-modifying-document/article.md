# Modifying the document

DOM modification is the key to creating "live" pages.

Here we'll see how to create new elements "on the fly" and modify the existing page content.

## Example: show a message

Let's demonstrate using an example. We'll add a message on the page that looks nicer than `alert`.

Here's how it will look:

\`\`\`html autorun height="80"

  
.alert {  
  padding: 15px;  
  border: 1px solid \#d6e9c6;  
  border-radius: 4px;  
  color: \#3c763d;  
  background-color: \#dff0d8;  
}  


_!_

 **Hi there!** You've read an important message. \*/!\* \`\`\` That was an HTML example. Now let's create the same \`div\` with JavaScript \(assuming that the styles are in the HTML or an external CSS file\). \#\# Creating an element To create DOM nodes, there are two methods: \`document.createElement\(tag\)\` : Creates a new \*element node\* with the given tag: \`\`\`js let div = document.createElement\('div'\); \`\`\` \`document.createTextNode\(text\)\` : Creates a new \*text node\* with the given text: \`\`\`js let textNode = document.createTextNode\('Here I am'\); \`\`\` \#\#\# Creating the message In our case the message is a \`div\` with \`alert\` class and the HTML in it: \`\`\`js let div = document.createElement\('div'\); div.className = "alert"; div.innerHTML = "**Hi there!** You've read an important message."; \`\`\` We created the element, but as of now it's only in a variable. We can't see the element on the page, as it's not yet a part of the document. \#\# Insertion methods To make the \`div\` show up, we need to insert it somewhere into \`document\`. For instance, in \`document.body\`. There's a special method \`append\` for that: \`document.body.append\(div\)\`. Here's the full code: \`\`\`html run height="80"  
.alert {  
  padding: 15px;  
  border: 1px solid \#d6e9c6;  
  border-radius: 4px;  
  color: \#3c763d;  
  background-color: \#dff0d8;  
}  
  
  let div = document.createElement\('div'\);  
  div.className = "alert";  
  div.innerHTML = "&lt;strong&gt;Hi there!&lt;/strong&gt; You've read an important message.";  
  
\*!\*  
  document.body.append\(div\);  
\*/!\*  
 \`\`\` This set of methods provides more ways to insert: - \`node.append\(...nodes or strings\)\` -- append nodes or strings at the end of \`node\`, - \`node.prepend\(...nodes or strings\)\` -- insert nodes or strings at the beginning of \`node\`, - \`node.before\(...nodes or strings\)\` –- insert nodes or strings before \`node\`, - \`node.after\(...nodes or strings\)\` –- insert nodes or strings after \`node\`, - \`node.replaceWith\(...nodes or strings\)\` –- replaces \`node\` with the given nodes or strings. Here's an example of using these methods to add items to a list and the text before/after it: \`\`\`html autorun

1. 0
2. 1
3. 2

  
  ol.before\('before'\); // insert string "before" before &lt;ol&gt;  
  ol.after\('after'\); // insert string "after" after &lt;ol&gt;  
  
  let liFirst = document.createElement\('li'\);  
  liFirst.innerHTML = 'prepend';  
  ol.prepend\(liFirst\); // insert liFirst at the beginning of &lt;ol&gt;  
  
  let liLast = document.createElement\('li'\);  
  liLast.innerHTML = 'append';  
  ol.append\(liLast\); // insert liLast at the end of &lt;ol&gt;  
 \`\`\` Here's a visual picture what methods do: !\[\]\(before-prepend-append-after.svg\) So the final list will be: \`\`\`html before

1. prepend
2. 0
3. 1
4. 2
5. append

 after \`\`\` These methods can insert multiple lists of nodes and text pieces in a single call. For instance, here a string and an element are inserted: \`\`\`html run  
  div.before\('&lt;p&gt;Hello&lt;/p&gt;', document.createElement\('hr'\)\);  
 \`\`\` All text is inserted \*as text\*. So the final HTML is: \`\`\`html run \*!\* &lt;p&gt;Hello&lt;/p&gt; \*/!\*

 \`\`\` In other words, strings are inserted in a safe way, like \`elem.textContent\` does it. So, these methods can only be used to insert DOM nodes or text pieces. But what if we want to insert HTML "as html", with all tags and stuff working, like \`elem.innerHTML\`? \#\# insertAdjacentHTML/Text/Element For that we can use another, pretty versatile method: \`elem.insertAdjacentHTML\(where, html\)\`. The first parameter is a code word, specifying where to insert relative to \`elem\`. Must be one of the following: - \`"beforebegin"\` -- insert \`html\` immediately before \`elem\`, - \`"afterbegin"\` -- insert \`html\` into \`elem\`, at the beginning, - \`"beforeend"\` -- insert \`html\` into \`elem\`, at the end, - \`"afterend"\` -- insert \`html\` immediately after \`elem\`. The second parameter is an HTML string, that is inserted "as HTML". For instance: \`\`\`html run  
  div.insertAdjacentHTML\('beforebegin', '&lt;p&gt;Hello&lt;/p&gt;'\);  
  div.insertAdjacentHTML\('afterend', '&lt;p&gt;Bye&lt;/p&gt;'\);  
 \`\`\` ...Would lead to: \`\`\`html run

Hello

Bye \`\`\` That's how we can append arbitrary HTML to the page. Here's the picture of insertion variants: !\[\]\(insert-adjacent.svg\) We can easily notice similarities between this and the previous picture. The insertion points are actually the same, but this method inserts HTML. The method has two brothers: - \`elem.insertAdjacentText\(where, text\)\` -- the same syntax, but a string of \`text\` is inserted "as text" instead of HTML, - \`elem.insertAdjacentElement\(where, elem\)\` -- the same syntax, but inserts an element. They exist mainly to make the syntax "uniform". In practice, only \`insertAdjacentHTML\` is used most of the time. Because for elements and text, we have methods \`append/prepend/before/after\` -- they are shorter to write and can insert nodes/text pieces. So here's an alternative variant of showing a message: \`\`\`html run  
.alert {  
  padding: 15px;  
  border: 1px solid \#d6e9c6;  
  border-radius: 4px;  
  color: \#3c763d;  
  background-color: \#dff0d8;  
}  
  
  document.body.insertAdjacentHTML\("afterbegin", \`&lt;div class="alert"&gt;  
    &lt;strong&gt;Hi there!&lt;/strong&gt; You've read an important message.  
  &lt;/div&gt;\`\);  
 \`\`\` \#\# Node removal To remove a node, there's a method \`node.remove\(\)\`. Let's make our message disappear after a second: \`\`\`html run untrusted  
.alert {  
  padding: 15px;  
  border: 1px solid \#d6e9c6;  
  border-radius: 4px;  
  color: \#3c763d;  
  background-color: \#dff0d8;  
}  
  
  let div = document.createElement\('div'\);  
  div.className = "alert";  
  div.innerHTML = "&lt;strong&gt;Hi there!&lt;/strong&gt; You've read an important message.";  
  
  document.body.append\(div\);  
\*!\*  
  setTimeout\(\(\) =&gt; div.remove\(\), 1000\);  
\*/!\*  
 \`\`\` Please note: if we want to \*move\* an element to another place -- there's no need to remove it from the old one. \*\*All insertion methods automatically remove the node from the old place.\*\* For instance, let's swap elements: \`\`\`html run height=50FirstSecond  
  // no need to call remove  
  second.after\(first\); // take \#second and after it insert \#first  
 \`\`\` \#\# Cloning nodes: cloneNode How to insert one more similar message? We could make a function and put the code there. But the alternative way would be to \*clone\* the existing \`div\` and modify the text inside it \(if needed\). Sometimes when we have a big element, that may be faster and simpler. - The call \`elem.cloneNode\(true\)\` creates a "deep" clone of the element -- with all attributes and subelements. If we call \`elem.cloneNode\(false\)\`, then the clone is made without child elements. An example of copying the message: \`\`\`html run height="120"  
.alert {  
  padding: 15px;  
  border: 1px solid \#d6e9c6;  
  border-radius: 4px;  
  color: \#3c763d;  
  background-color: \#dff0d8;  
}  
 **Hi there!** You've read an important message.

 _!_ let div2 = div.cloneNode\(true\); // clone the message div2.querySelector\('strong'\).innerHTML = 'Bye there!'; // change the clone

div.after\(div2\); // show the clone after the existing div _/!_ &lt;/script&gt;

```text
## DocumentFragment [#document-fragment]

`DocumentFragment` is a special DOM node that serves as a wrapper to pass around lists of nodes.

We can append other nodes to it, but when we insert it somewhere, then its content is inserted instead.

For example, `getListContent` below generates a fragment with `<li>` items, that are later inserted into `<ul>`:

```html run
<ul id="ul"></ul>

<script>
function getListContent() {
  let fragment = new DocumentFragment();

  for(let i=1; i<=3; i++) {
    let li = document.createElement('li');
    li.append(i);
    fragment.append(li);
  }

  return fragment;
}

*!*
ul.append(getListContent()); // (*)
*/!*
</script>
```

Please note, at the last line `(*)` we append `DocumentFragment`, but it "blends in", so the resulting structure will be:

```markup
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```

`DocumentFragment` is rarely used explicitly. Why append to a special kind of node, if we can return an array of nodes instead? Rewritten example:

\`\`\`html run

 function getListContent\(\) { let result = \[\];

for\(let i=1; i&lt;=3; i++\) { let li = document.createElement\('li'\); li.append\(i\); result.push\(li\); }

return result; }

_!_ ul.append\(...getListContent\(\)\); // append + "..." operator = friends! _/!_ &lt;/script&gt;

```text
We mention `DocumentFragment` mainly because there are some concepts on top of it, like [template](info:template-element) element, that we'll cover much later.

## Old-school insert/remove methods

[old]

There are also "old school" DOM manipulation methods, existing for historical reasons.

These methods come from really ancient times. Nowadays, there's no reason to use them, as modern methods, such as `append`, `prepend`, `before`, `after`, `remove`, `replaceWith`, are more flexible.

The only reason we list these methods here is that you can find them in many old scripts:

`parentElem.appendChild(node)`
: Appends `node` as the last child of `parentElem`.

    The following example adds a new `<li>` to the end of `<ol>`:

    ```html run height=100
    <ol id="list">
      <li>0</li>
      <li>1</li>
      <li>2</li>
    </ol>

    <script>
      let newLi = document.createElement('li');
      newLi.innerHTML = 'Hello, world!';

      list.appendChild(newLi);
    </script>
```

`parentElem.insertBefore(node, nextSibling)` : Inserts `node` before `nextSibling` into `parentElem`.

```text
The following code inserts a new list item before the second `<li>`:

```html run height=100
<ol id="list">
  <li>0</li>
  <li>1</li>
  <li>2</li>
</ol>
<script>
  let newLi = document.createElement('li');
  newLi.innerHTML = 'Hello, world!';

*!*
  list.insertBefore(newLi, list.children[1]);
*/!*
</script>
```
To insert `newLi` as the first element, we can do it like this:

```js
list.insertBefore(newLi, list.firstChild);
```
```

`parentElem.replaceChild(node, oldChild)` : Replaces `oldChild` with `node` among children of `parentElem`.

`parentElem.removeChild(node)` : Removes `node` from `parentElem` \(assuming `node` is its child\).

```text
The following example removes first `<li>` from `<ol>`:

```html run height=100
<ol id="list">
  <li>0</li>
  <li>1</li>
  <li>2</li>
</ol>

<script>
  let li = list.firstElementChild;
  list.removeChild(li);
</script>
```
```

All these methods return the inserted/removed node. In other words, `parentElem.appendChild(node)` returns `node`. But usually the returned value is not used, we just run the method.

## A word about "document.write"

There's one more, very ancient method of adding something to a web-page: `document.write`.

The syntax:

\`\`\`html run

Somewhere in the page... _!_

 document.write\(&apos;&lt;b&gt;Hello from JS&lt;/b&gt;&apos;\);  _/!_

The end

```text
The call to `document.write(html)` writes the `html` into page "right here and now". The `html` string can be dynamically generated, so it's kind of flexible. We can use JavaScript to create a full-fledged webpage and write it.

The method comes from times when there was no DOM, no standards... Really old times. It still lives, because there are scripts using it.

In modern scripts we can rarely see it, because of the following important limitation:

**The call to `document.write` only works while the page is loading.**

If we call it afterwards, the existing document content is erased.

For instance:

```html run
<p>After one second the contents of this page will be replaced...</p>
*!*
<script>
  // document.write after 1 second
  // that's after the page loaded, so it erases the existing content
  setTimeout(() => document.write('<b>...By this.</b>'), 1000);
</script>
*/!*
```

So it's kind of unusable at "after loaded" stage, unlike other DOM methods we covered above.

That's the downside.

There's an upside also. Technically, when `document.write` is called while the browser is reading \("parsing"\) incoming HTML, and it writes something, the browser consumes it just as if it were initially there, in the HTML text.

So it works blazingly fast, because there's _no DOM modification_ involved. It writes directly into the page text, while the DOM is not yet built.

So if we need to add a lot of text into HTML dynamically, and we're at page loading phase, and the speed matters, it may help. But in practice these requirements rarely come together. And usually we can see this method in scripts just because they are old.

## Summary

* Methods to create new nodes:
  * `document.createElement(tag)` -- creates an element with the given tag,
  * `document.createTextNode(value)` -- creates a text node \(rarely used\),
  * `elem.cloneNode(deep)` -- clones the element, if `deep==true` then with all descendants.  
* Insertion and removal:
  * `node.append(...nodes or strings)` -- insert into `node`, at the end,
  * `node.prepend(...nodes or strings)` -- insert into `node`, at the beginning,
  * `node.before(...nodes or strings)` –- insert right before `node`,
  * `node.after(...nodes or strings)` –- insert right after `node`,
  * `node.replaceWith(...nodes or strings)` –- replace `node`.
  * `node.remove()` –- remove the `node`.

    Text strings are inserted "as text".
* There are also "old school" methods:
  * `parent.appendChild(node)`
  * `parent.insertBefore(node, nextSibling)`
  * `parent.removeChild(node)`
  * `parent.replaceChild(newElem, node)`

    All these methods return `node`.
* Given some HTML in `html`, `elem.insertAdjacentHTML(where, html)` inserts it depending on the value of `where`:
  * `"beforebegin"` -- insert `html` right before `elem`,
  * `"afterbegin"` -- insert `html` into `elem`, at the beginning,
  * `"beforeend"` -- insert `html` into `elem`, at the end,
  * `"afterend"` -- insert `html` right after `elem`.

    Also there are similar methods, `elem.insertAdjacentText` and `elem.insertAdjacentElement`, that insert text strings and elements, but they are rarely used.
* To append HTML to the page before it has finished loading:
  * `document.write(html)`

    After the page is loaded such a call erases the document. Mostly seen in old scripts.
