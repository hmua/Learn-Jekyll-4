---
tweets:
  - date: 2023-06-29 00:00:00 +0000
    t:
    - |-
      通商 通路 流通 干支通路
      背景好时惠及全民 背景坏时搜刮民脂
  - date: 2023-06-26 00:00:00 +0000
    t:
    - |-
      ♂利器 锐器 锋 刃 好钢 力气都花在准备这里
      传统技法 水滴
    - |-
      从专业转向公共事业
      空间从私人领域转向公共领域
      新开发的庞大空旷的公共空间
      让固守私人领域失去价值 甚至成为累赘
  - date: 2023-06-28 00:00:00 +0000
    t:
    - 基本像个集合，基本前面的变动是集合中每个成员的定义
    - "🌙这些表象 都见过 都熟悉\n实际 表象之后在发生着什么？"
  - date: 2023-06-27 00:00:00 +0000
    t:
    - |-
      盲人摸象 有人摸的鼻子 有人摸的耳朵 有人摸的牙
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
- {{ post.slug }} *po*
{% else %}{%for t in post.t reversed%}
- {{t}} *tw*
{% endfor%}{% endif %}{% endfor%}{% endfor%}
