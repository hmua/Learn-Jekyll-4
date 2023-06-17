{%for a in site.pages-%}
{{a[0]}}|{{a[1]}}|{{a.first}}|{{a.last}}|{{a|first}}|{{a|last}}|1
{%endfor%}
