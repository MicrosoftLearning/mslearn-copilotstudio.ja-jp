---
title: オンラインでホストされる手順
permalink: index.html
layout: home
---

# Copilot Studio の演習

Microsoft Learn の Copilot Studio 演習へのリンクを以下に示します。

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %} {% for activity in labs  %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
