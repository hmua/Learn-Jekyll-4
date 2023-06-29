---
tweets:
  2023-6-29:
    - 通商 通路 流通 干支通路
      背景好时惠及全民 背景坏时搜刮民脂
  2023-6-26:
    - ♂利器 锐器 锋 刃 好钢 力气都花在准备这里
      传统技法 水滴
    - 从专业转向公共事业
      空间从私人领域转向公共领域
      新开发的庞大空旷的公共空间
      让固守私人领域失去价值 甚至成为累赘
  2023-6-28:
    - 基本像个集合，基本前面的变动是集合中每个成员的定义
    - 🌙这些表象 都见过 都熟悉
      实际 表象之后在发生着什么？
  2023-6-27:
    - 盲人摸象 有人摸的鼻子 有人摸的耳朵 有人摸的牙
      有人摸的屁股 有人摸的尾巴
      各保存 描述各的讯息

---
{{site.posts|group_by:'date'}}✓
{{page.tweets}}✓

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
