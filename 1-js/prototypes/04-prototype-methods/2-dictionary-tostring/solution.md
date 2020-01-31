# solution

The method can take all enumerable keys using `Object.keys` and output their list.

To make `toString` non-enumerable, let's define it using a property descriptor. The syntax of `Object.create` allows us to provide an object with property descriptors as the second argument.

\`\`\`js run _!_ let dictionary = Object.create\(null, { toString: { // define toString property value\(\) { // the value is a function return Object.keys\(this\).join\(\); } } }\); _/!_

dictionary.apple = "Apple"; dictionary.**proto** = "test";

// apple and **proto** is in the loop for\(let key in dictionary\) { alert\(key\); // "apple", then "**proto**" }

// comma-separated list of properties by toString alert\(dictionary\); // "apple,**proto**"

\`\`\`

When we create a property using a descriptor, its flags are `false` by default. So in the code above, `dictionary.toString` is non-enumerable.

See the the chapter  for review.

