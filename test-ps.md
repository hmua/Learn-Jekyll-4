{%for a in site.pages-%}
a.path|
{%-unless a.path=='test-ps.md'-%}
1{{a[0]}}|2{{a[1]}}|3{{a.first|replace:'|','-'}}|4{{a.last}}|5{{a|first}}|6{{a|last|replace:'|','-':replace:'<','-'}}
{%-endunless%}
{%endfor%}
