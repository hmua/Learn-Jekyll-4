{%assign a=site.pages|where:'path','test.md'|first%}
```kramdown
{{a|join:'、'}}
```

---
{%for b in a%}
- {{b}}{%endfor%}

---
{%for b in a%}
- {{b[0]}}: {{b[1]}}{%endfor%}

---
{%for b in a%}
- {{b.first}}: {{b.last}}{%endfor%}

---
{{a|replace:replace:'<','&lt;'}}

---

{%for a in site.pages-%}
{{a.path}}|
{%-unless a.path=='test-ps.md'or a.path=='assets/css/style.scss'-%}
1{{a[0]}}|2{{a[1]}}|7{{a[2]}}|8{{a[3]-}}
|3{{a.first|replace:'|','&vert;'|replace:'<','&lt;'}}|4{{a.last-}}
|5{{a|first|replace:'|','&vert;'|replace:'<','&lt;'-}}|6{{a|last-}}
|9{{a|replace:'|','&vert;'|replace:'<','&lt;'-}}
{%endunless%}
{%endfor%}
