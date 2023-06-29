---
tweets:
  - date: 2023-06-29 00:00:00 +0000
    t:
    - 通商 通路 流通 干支通路
      背景好时惠及全民 背景坏时搜刮民脂
  - date: 2023-06-26 00:00:00 +0000
    t:
    - ♂利器 锐器 锋 刃 好钢 力气都花在准备这里
      传统技法 水滴
    - 从专业转向公共事业
      空间从私人领域转向公共领域
      新开发的庞大空旷的公共空间
      让固守私人领域失去价值 甚至成为累赘
  - date: 2023-06-28 00:00:00 +0000
    t:
    - 基本像个集合，基本前面的变动是集合中每个成员的定义
    - 🌙这些表象 都见过 都熟悉
      实际 表象之后在发生着什么？
  - date: 2023-06-27 00:00:00 +0000
    t:
    - 盲人摸象 有人摸的鼻子 有人摸的耳朵 有人摸的牙
      有人摸的屁股 有人摸的尾巴
      各保存 描述各的讯息
---
{{site.posts|group_by:'date'}}

---
{{page.tweets|group_by:'date'}}✓

---
{{site.posts|concat:page.tweets|group_by:'date'|map:'name'|sort|join:', '}}

---
{%assign by_day=site.posts|concat:page.tweets|group_by:'date'|sort:'name'%}
{%for day in by_day reversed%}
###### {{day.name|date:'%Y-%m-%d'}}
{% for post in day.items%}{% if post.collection == 'posts'%}
- {{ post.slug }} *post*
{% else %}{%for t in post.t reversed%}
- {{t}} *twi*
{% endfor%}{% endif %}{% endfor%}{% endfor%}

---
```json
{{site.posts|concat:page.tweets|group_by:'date'|sort:'name'}}
```

---
{%assign tweets=page.tweets%}
{%for a in tweets-%}
1. {{a}}
{%endfor%}
✓`for`迭代可以

---

{%for a in tweets-%}
1|{{a[0]}}|2|{{a[1]}}
{%endfor%}
`i[0]`和`i[1]`都无输出

---

{%for i in tweets-%}
1|{{i|first}}|2|{{i|last}}
{%endfor%}
`i|first`有输出

{{tweets|map:'first'}}
×但不支持`map:'first'`

---
{{tweets|map:'date'|join:', '}}
`map:'date'|join:', '`

---
{{tweets|sort:'dafote'}}
`sort:'date'`

---
{%assign a=tweets|map:'first'-%}
{{a}}×

{{a|join:', '}}×

{%for i in a-%}
1|{{i}}|2|{{i|first}}|3|{{i|last}}
{%endfor%}
×map后可以join也可以for，有条目但没有值，找不到数据在哪

---

{%for i in tweets-%}
{%assign j=i.first-%}
1|{{j[0]}}|2|{{j[1]}}
{%endfor%}

---

{%for i in tweets-%}
{%assign j=i.first-%}
1|{{j|first}}|2|{{j|last}}
{%endfor%}

居然是和第一轮一样`i[0]`和`i[1]`都无输出，`i|first`有输出
`i|first`是不是能一直叠下去？试一下——

{%for i in tweets-%}
1. {{i|first}}
{%endfor%}

✓有输出

{%for i in tweets-%}
1. {{i|first|first}}
{%endfor%}

✓输出日期部分

{%for i in tweets-%}
1. {{i.first|first}}
{%endfor%}

✓输出日期部分

{%for i in tweets-%}
1. {{i|first|first|first}}
{%endfor%}
^
{%for a in tweets-%}
1. {{i|first|first|first|first|first}}
{%endfor%}
^
{%for i in tweets-%}
1. {{i.first.first.first}}
{%endfor%}

×叠三个以上`|first`则都无输出

---

{%for i in tweets-%}
1|{{i|first|first}}|2|{{i|first|last}}
{%endfor%}

---

#### 小结
map不到日期部分，也就不知道怎样`group_by`、排序，看来都无法做
