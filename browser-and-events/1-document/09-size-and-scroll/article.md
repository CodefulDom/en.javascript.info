# Element size and scrolling

There are many JavaScript properties that allow us to read information about element width, height and other geometry features.

We often need them when moving or positioning elements in JavaScript.

## Sample element

As a sample element to demonstrate properties we'll use the one given below:

\`\`\`html no-beautify

 ...Text...  
  \#example {  
    width: 300px;  
    height: 200px;  
    border: 25px solid \#E8C48F;  
    padding: 20px;                
    overflow: auto;               
  }  
 \`\`\` It has the border, padding and scrolling. The full set of features. There are no margins, as they are not the part of the element itself, and there are no special properties for them. The element looks like this: !\[\]\(metric-css.svg\) You can \[open the document in the sandbox\]\(sandbox:metric\). \`\`\`smart header="Mind the scrollbar" The picture above demonstrates the most complex case when the element has a scrollbar. Some browsers \(not all\) reserve the space for it by taking it from the content \(labeled as "content width" above\). So, without scrollbar the content width would be \`300px\`, but if the scrollbar is \`16px\` wide \(the width may vary between devices and browsers\) then only \`300 - 16 = 284px\` remains, and we should take it into account. That's why examples from this chapter assume that there's a scrollbar. Without it, some calculations are simpler. \`\`\` \`\`\`smart header="The \`padding-bottom\` area may be filled with text" Usually paddings are shown empty on our illustrations, but if there's a lot of text in the element and it overflows, then browsers show the "overflowing" text at \`padding-bottom\`, that's normal. \`\`\` \#\# Geometry Here's the overall picture with geometry properties: !\[\]\(metric-all.svg\) Values of these properties are technically numbers, but these numbers are "of pixels", so these are pixel measurements. Let's start exploring the properties starting from the outside of the element. \#\# offsetParent, offsetLeft/Top These properties are rarely needed, but still they are the "most outer" geometry properties, so we'll start with them. The \`offsetParent\` is the nearest ancestor that the browser uses for calculating coordinates during rendering. That's the nearest ancestor that is one of the following: 1. CSS-positioned \(\`position\` is \`absolute\`, \`relative\`, \`fixed\` or \`sticky\`\), or 2. \`

| \`, \` |
| :--- |


element.style.height = `${element.scrollHeight}px`

```text
## scrollLeft/scrollTop

Properties `scrollLeft/scrollTop` are the width/height of the hidden, scrolled out part of the element.

On the picture below we can see `scrollHeight` and `scrollTop` for a block with a vertical scroll.

![](metric-scroll-top.svg)

In other words, `scrollTop` is "how much is scrolled up".

````smart header="`scrollLeft/scrollTop` can be modified"
Most of the geometry properties here are read-only, but `scrollLeft/scrollTop` can be changed, and the browser will scroll the element.

```online
If you click the element below, the code `elem.scrollTop += 10` executes. That makes the element content scroll `10px` down.

<div onclick="this.scrollTop+=10" style="cursor:pointer;border:1px solid black;width:100px;height:80px;overflow:auto">Click<br>Me<br>1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9</div>
```

Setting `scrollTop` to `0` or `Infinity` will make the element scroll to the very top/bottom respectively.

```text
## Don't take width/height from CSS

We've just covered geometry properties of DOM elements, that can be used to get widths, heights and calculate distances.

But as we know from the chapter <info:styles-and-classes>, we can read CSS-height and width using `getComputedStyle`.

So why not to read the width of an element with `getComputedStyle`, like this?

```js run
let elem = document.body;

alert( getComputedStyle(elem).width ); // show CSS width for elem
```

Why should we use geometry properties instead? There are two reasons:

1. First, CSS `width/height` depend on another property: `box-sizing` that defines "what is" CSS width and height. A change in `box-sizing` for CSS purposes may break such JavaScript.
2. Second, CSS `width/height` may be `auto`, for instance for an inline element:

   \`\`\`html run Hello!

    &lt;em&gt;!&lt;/em&gt; alert\( getComputedStyle\(elem\).width \); // auto &lt;em&gt;/&lt;/em&gt;&lt;em&gt;!&lt;/em&gt; 

   \`\`\`

   From the CSS standpoint, `width:auto` is perfectly normal, but in JavaScript we need an exact size in `px` that we can use in calculations. So here CSS width is useless.

And there's one more reason: a scrollbar. Sometimes the code that works fine without a scrollbar becomes buggy with it, because a scrollbar takes the space from the content in some browsers. So the real width available for the content is _less_ than CSS width. And `clientWidth/clientHeight` take that into account.

...But with `getComputedStyle(elem).width` the situation is different. Some browsers \(e.g. Chrome\) return the real inner width, minus the scrollbar, and some of them \(e.g. Firefox\) -- CSS width \(ignore the scrollbar\). Such cross-browser differences is the reason not to use `getComputedStyle`, but rather rely on geometry properties.

```text
If your browser reserves the space for a scrollbar (most browsers for Windows do), then you can test it below.

[iframe src="cssWidthScroll" link border=1]

The element with text has CSS `width:300px`.

On a Desktop Windows OS, Firefox, Chrome, Edge all reserve the space for the scrollbar. But  Firefox shows `300px`, while Chrome and Edge show less. That's because Firefox returns the CSS width and other browsers return the "real" width.
```

Please note that the described difference is only about reading `getComputedStyle(...).width` from JavaScript, visually everything is correct.

## Summary

Elements have the following geometry properties:

* `offsetParent` -- is the nearest positioned ancestor or `td`, `th`, `table`, `body`.
* `offsetLeft/offsetTop` -- coordinates relative to the upper-left edge of `offsetParent`.
* `offsetWidth/offsetHeight` -- "outer" width/height of an element including borders.
* `clientLeft/clientTop` -- the distances from the upper-left outer corner to the upper-left inner \(content + padding\) corner. For left-to-right OS they are always the widths of left/top borders. For right-to-left OS the vertical scrollbar is on the left so `clientLeft` includes its width too.
* `clientWidth/clientHeight` -- the width/height of the content including paddings, but without the scrollbar.
* `scrollWidth/scrollHeight` -- the width/height of the content, just like `clientWidth/clientHeight`, but also include scrolled-out, invisible part of the element.
* `scrollLeft/scrollTop` -- width/height of the scrolled out upper part of the element, starting from its upper-left corner.

All properties are read-only except `scrollLeft/scrollTop` that make the browser scroll the element if changed.

