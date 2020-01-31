# solution

That's because the child constructor must call `super()`.

Here's the corrected code:

\`\`\`js run class Animal {

constructor\(name\) { this.name = name; }

}

class Rabbit extends Animal { constructor\(name\) {  
_!_ super\(name\); _/!_ this.created = Date.now\(\); } }

_!_ let rabbit = new Rabbit\("White Rabbit"\); // ok now _/!_ alert\(rabbit.name\); // White Rabbit

\`\`\`

