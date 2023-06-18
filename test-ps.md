{%assign a=site.pages|where:'path','test.md'|first%}
```yaml
{{a}}
```

---
```yaml
{{a|join:'、'}}
```
*`join`是无效的，搞不懂，
for是一个handle一条，但join就是整个一条。

---
{%for a in a%}
- {{a}}{%endfor%}
✓

---
{%for b in a%}
- {{b}}{%endfor%}
✓

---
{%for b in a%}- {{b}}\n{%endfor%}
✓

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
