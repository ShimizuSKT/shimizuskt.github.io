---
layout: page
title: "Tags"
description: "哈哈，你找到了我的文章基因库"  
header-img: "img/semantic.jpg"  
---

<style>
  /* 简单美化标签云和列表 */
  #tag_cloud {
    margin: 2rem 0;
    text-align: center;
  }
  #tag_cloud a {
    display: inline-block;
    margin: 0.3rem 0.6rem;
    padding: 0.2rem 0.8rem;
    background: #f0f0f0;
    border-radius: 20px;
    color: #333;
    text-decoration: none;
    transition: all 0.2s ease;
    font-size: 0.9rem;
  }
  #tag_cloud a:hover {
    background: #ffb6c1;
    color: #fff;
    transform: scale(1.05);
  }
  .listing {
    list-style: none;
    padding-left: 0;
  }
  .listing-seperator {
    font-size: 1.5rem;
    font-weight: bold;
    margin-top: 1.5rem;
    margin-bottom: 0.8rem;
    border-bottom: 2px solid #ffb6c1;
    display: inline-block;
    padding-bottom: 0.2rem;
  }
  .listing-item {
    margin: 0.6rem 0;
    padding: 0.3rem 0;
    border-bottom: 1px dashed #eee;
  }
  .listing-item time {
    font-family: monospace;
    color: #888;
    margin-right: 1rem;
  }
  .listing-item a {
    color: #2c3e50;
    text-decoration: none;
    font-weight: 500;
  }
  .listing-item a:hover {
    color: #ff6b81;
    text-decoration: underline;
  }
</style>

## 本页使用方法

1. 在下面选一个你喜欢的词
2. 点击它
3. 相关的文章会「唰」地一声跳到页面顶端
4. 马上试试？

## 基因列表

<div id='tag_cloud'>
{% for tag in site.tags %}
<a href="#{{ tag[0] }}" title="{{ tag[0] }}" rel="{{ tag[1].size }}">{{ tag[0] }}</a>
{% endfor %}
</div>

<ul class="listing">
{% for tag in site.tags %}
  <li class="listing-seperator" id="{{ tag[0] }}">{{ tag[0] }}</li>
{% for post in tag[1] %}
  <li class="listing-item">
  <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
  <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
  </li>
{% endfor %}
{% endfor %}
</ul>

<script src="/media/js/jquery.tagcloud.js" type="text/javascript" charset="utf-8"></script> 
<script language="javascript">
$.fn.tagcloud.defaults = {
    size: {start: 1, end: 1, unit: 'em'},
      color: {start: '#f8e0e6', end: '#ff3333'}
};

$(function () {
    $('#tag_cloud a').tagcloud();
});
</script>