---
layout: post
title: "Script Test World"
tags: [test]
comments: true
---

대충 테스트하는곳

---

<div id="monaco" style="height:60vh;"></div>
  
<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.3.6/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.16.2/min/vs/loader.js"></script>
<script>
    var editor;
    
    require.config({ paths: { 'vs': 'https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.16.2/min/vs' }});
    require(['vs/editor/editor.main'], function() {
      editor = monaco.editor.create(document.getElementById('monaco'), {
        theme: 'vs-dark',
        fontFamily: 'Nanum Gothic Coding',
        automaticLayout: true,
        language: 'javascript',
        value: 'alert("Hello, World!")'
      });
    });
</script>
<br>
<input type="button" value="실행" onclick="try {eval(editor.getValue())} catch (e) {alert(e)}">