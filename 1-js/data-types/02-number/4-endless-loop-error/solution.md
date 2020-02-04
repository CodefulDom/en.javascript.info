# solution

That's because `i` would never equal `10`.

Run it to see the _real_ values of `i`:

\`\`\`js run let i = 0; while \(i &lt; 11\) { i += 0.2; if \(i &gt; 9.8 && i &lt; 10.2\) alert\( i \); }

\`\`\`

None of them is exactly `10`.

Such things happen because of the precision losses when adding fractions like `0.2`.

Conclusion: evade equality checks when working with decimal fractions.

