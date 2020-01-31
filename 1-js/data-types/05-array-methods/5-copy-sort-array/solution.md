# solution

We can use `slice()` to make a copy and run the sort on it:

\`\`\`js run function copySorted\(arr\) { return arr.slice\(\).sort\(\); }

let arr = \["HTML", "JavaScript", "CSS"\];

_!_ let sorted = copySorted\(arr\); _/!_

alert\( sorted \); alert\( arr \);

\`\`\`

