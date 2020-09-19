---
layout: post
title: "Script Test World"
tags: [test]
comments: true
---

대충 테스트하는곳

---

<textarea id="scr" rows="10" cols="50">
alert("Hello, World!")
</textarea>
<input type="button" value="실행" onclick="try {eval(document.getElementById('scr').value)} catch (e) {alert(e)}">
