---
permalink: /探针
---
# Jekyll版本探针 测试
*根据[Liquid Filters | Jekyll • Simple, blog-aware, static sites](https://jekyllrb.com/docs/liquid/filters/)制作*
*根据[Dependency versions \| GitHub Pages](https://pages.github.com/versions/)，GitHub Pages默认使用Jekyll 3.9.3*

{%assign a='a,bc,def,hijk,a,bc,def'|split:','%}
{{a|size}}
{{a|join:','}}
{{a.size}}
{{a.join:','}}×
{{a.first.size}}

### Map
{{a|map:'upcase'}}
{{site.pages|map:'path'|join:','}}，预期*assets/css/style.scss,README.md*✓

### Where
{%assign pages=site.pages|where:'path','assets/css/style.scss'%}
{{pages.size}}，预期*1*
{{pages.first.name}}，预期*style.scss*✓

### Where Expression (≥3.2.0)
{{a|where_exp:'b','b=="a"'}}，预期*aa*✓

### Binary operators in `where_exp` filter (≥4.0)
{{'{'}}{ a | where_exp:"b", "b=='a' or b=='bc'" }}
`gh-pages` classic：*build error*；新版：*abcabc*✓

### Detecting `nil` values with `where` filter (≥4.0)
{%assign a=site.pages|where:'my_prop',nil%}
{{a.size}}
`gh-pages` classic：*8*；新版：*5*✓

### Find (≥4.1.0)
{%assign aCss='assets/main.scss'%}
{%assign a=site.pages|find:'path',aCss%}
{{a.name}}

`gh-pages` classic：*无输出*，*`|find`忽略了*
新版：*main.scss*×

### 行内注释 (Liquid ≥5.4)
`{{'{'}}% # ... ... %}`（不支持）
