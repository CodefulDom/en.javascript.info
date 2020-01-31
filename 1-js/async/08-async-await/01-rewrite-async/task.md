# Rewrite using async/await

Rewrite this example code from the chapter  using `async/await` instead of `.then/catch`:

\`\`\`js run function loadJson\(url\) { return fetch\(url\) .then\(response =&gt; { if \(response.status == 200\) { return response.json\(\); } else { throw new Error\(response.status\); } }\) }

loadJson\('no-such-user.json'\) .catch\(alert\); // Error: 404

\`\`\`

