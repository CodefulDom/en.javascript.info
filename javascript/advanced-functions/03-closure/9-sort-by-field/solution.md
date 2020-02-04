# solution

\`\`\`js run let users = \[ { name: "John", age: 20, surname: "Johnson" }, { name: "Pete", age: 18, surname: "Peterson" }, { name: "Ann", age: 19, surname: "Hathaway" } \];

_!_ function byField\(field\) { return \(a, b\) =&gt; a\[field\] &gt; b\[field\] ? 1 : -1; } _/!_

users.sort\(byField\('name'\)\); users.forEach\(user =&gt; alert\(user.name\)\); // Ann, John, Pete

users.sort\(byField\('age'\)\); users.forEach\(user =&gt; alert\(user.name\)\); // Pete, Ann, John

\`\`\`

