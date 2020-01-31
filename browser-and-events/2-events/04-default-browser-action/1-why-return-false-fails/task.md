# task

importance: 3

## Why "return false" doesn't work?

Why in the code below `return false` doesn't work at all?

\`\`\`html autorun run

  
  function handler\(\) {  
    alert\( "..." \);  
    return false;  
  }  


[the browser will go to w3.org](https://w3.org)

\`\`\`

The browser follows the URL on click, but we don't want it.

How to fix?

