# solution

There's a catch here.

At the time of `<script>` execution the last DOM node is exactly `<script>`, because the browser did not process the rest of the page yet.

So the result is `1` \(element node\).

\`\`\`html run height=60

  
    alert\(document.body.lastChild.nodeType\);  
  

&lt;/html&gt;

\`\`\`

