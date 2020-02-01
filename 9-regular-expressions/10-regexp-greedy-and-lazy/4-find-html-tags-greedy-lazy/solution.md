# solution

The solution is `pattern:<[^<>]+>`.

\`\`\`js run let regexp = /&lt;+&gt;/g;

let str = '&lt;&gt;   ';

alert\( str.match\(regexp\) \); // '', '', ''

\`\`\`

