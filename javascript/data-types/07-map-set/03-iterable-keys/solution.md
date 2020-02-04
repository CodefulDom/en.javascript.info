# solution

That's because `map.keys()` returns an iterable, but not an array.

We can convert it into an array using `Array.from`:

\`\`\`js run let map = new Map\(\);

map.set\("name", "John"\);

_!_ let keys = Array.from\(map.keys\(\)\); _/!_

keys.push\("more"\);

alert\(keys\); // name, more

\`\`\`

