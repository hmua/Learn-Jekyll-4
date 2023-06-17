---
output: true
test_field: foobar
tweets:
  - 2022:
    - 6:
      - 16:
        some content
      - 17:
        some content 2
        some content 333
  - 2023:
    - 6:
      - 16:
        some content
        1616 16 16
      - 17:
        17171717
        some content 2
        some content 333
---
{{page.test_field}}
{{site.site_field}}

---
{{site.site_array}}

---
{{site.site_array[0]}}

---
{{site.site_array[1]}}

---
{%assign a=page.tweets%}
{{a}}

---
{{a[0]}}

---
{{a[1]}}

---
{{a[0][0]}}

---
{{a[0][1]}}

---
{{site.tweets}}

---
{{site.tweets[0]}}

---
{{site.tweets[1]}}

---
{{site.tweets[0][0]}}

---
{{site.tweets[0][1]}}

---
{{site.tweets['2023']}}

---
{{site.tweets["2023"]}}

---
{{site.tweets.2023}}

---
{{site.tweets[2023][6]}}

---
{{site.tweets[2023][6][17]}}

---
123
