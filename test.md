---
output: true
test_field: foobar
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
