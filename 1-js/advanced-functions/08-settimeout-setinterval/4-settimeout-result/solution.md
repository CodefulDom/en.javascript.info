# solution

Any `setTimeout` will run only after the current code has finished.

The `i` will be the last one: `100000000`.

\`\`\`js run let i = 0;

setTimeout\(\(\) =&gt; alert\(i\), 100\); // 100000000

// assume that the time to execute this function is &gt;100ms for\(let j = 0; j &lt; 100000000; j++\) { i++; }

\`\`\`

