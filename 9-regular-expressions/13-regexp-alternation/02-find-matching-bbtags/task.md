# Find bbtag pairs

A "bb-tag" looks like `[tag]...[/tag]`, where `tag` is one of: `b`, `url` or `quote`.

For instance:

```text
[b]text[/b]
[url]http://google.com[/url]
```

BB-tags can be nested. But a tag can't be nested into itself, for instance:

```text
Normal:
[url] [b]http://google.com[/b] [/url]
[quote] [b]text[/b] [/quote]

Can't happen:
[b][b]text[/b][/b]
```

Tags can contain line breaks, that's normal:

```text
[quote]
  [b]text[/b]
[/quote]
```

Create a regexp to find all BB-tags with their contents.

For instance:

```javascript
let regexp = /your regexp/flags;

let str = "..[url]http://google.com[/url]..";
alert( str.match(regexp) ); // [url]http://google.com[/url]
```

If tags are nested, then we need the outer tag \(if we want we can continue the search in its content\):

```javascript
let regexp = /your regexp/flags;

let str = "..[url][b]http://google.com[/b][/url]..";
alert( str.match(regexp) ); // [url][b]http://google.com[/b][/url]
```

