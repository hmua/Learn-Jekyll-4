---
---
{{site.site_field}}

---
{{site.site_array}}

---
{{site.site_array[0]}}

---
{{site.site_array[1]}}

---
{%assign a=site.tweets%}
{{a}}✓

---
{{a[0]}}✓

---
{{a[1]}}✓

---
{{a[0][0]}}×
{{a[0][1]}}×

---
{{a['2023']}}×
{{a["2023"]}}×

---
{{a.2023}}×
{{a[2023][6]}}×
{{a[2023][6][17]}}×
