# solution

Answer: **1 and 3**.

Both commands result in adding the `text` "as text" into the `elem`.

Here's an example:

\`\`\`html run height=80

 let text = '**text**';

elem1.append\(document.createTextNode\(text\)\); elem2.innerHTML = text; elem3.textContent = text; &lt;/script&gt;

\`\`\`

