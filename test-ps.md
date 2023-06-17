{%for a in site.pages-%}
{{a.path}}|
{%-unless a.path=='test-ps.md'or a.path=='assets/css/style.scss'-%}
1{{a[0]}}|2{{a[1]}}|7{{a[2]}}|8{{a[3]-}}
|3{{a.first|replace:'|','&vert;'|replace:'<','&lt;'-}}
|4{{a.last-}}
|5{{a|first|replace:'|','&vert;'|replace:'<','&lt;'-}}
|6{{a|last|replace:'|','&vert;'|replace:'<','&lt;'-}}
{%endunless%}
{%endfor%}
