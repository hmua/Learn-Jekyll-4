{%for a in site.pages-%}
1{{a[0]}}|2{{a[1]}}|3{{a.first|escape}}|4{{a.last}}|5{{a|first}}|6{{a|last}}
{%endfor%}
