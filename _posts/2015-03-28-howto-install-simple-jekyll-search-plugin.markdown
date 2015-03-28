---
layout: post
status: published
published: true
title: How to install simple-jekyll-search plugin
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['jekyll']
comments: []
---

With the goal of improve my blog, today I have installed the [Simple-Jeckyll-Search](http://www.jekyll-plugins.com/plugins/simple-jekyll-search) plugin. [Simple-Jekyll-Search](http://www.jekyll-plugins.com/plugins/simple-jekyll-search) is a JavaScript library to add search functionality to any Jekyll blog.

1.- Create a search.json in the document root.

```json
---
layout: none
---
[
  {% for post in site.posts %}
    {
      "title"    : "{{ post.title | escape }}",
      "category" : "{{ post.category }}",
      "tags"     : "{{ post.tags | join: ', ' }}",
      "url"      : "{{ site.baseurl }}{{ post.url }}",
      "date"     : "{{ post.date }}",
      "content"  : "{{ post.content | strip_html | strip_newlines }}"
    } {% unless forloop.last %},{% endunless %}
  {% endfor %}
]
```

2.- Download from git and add *jekyll-search.js* file in *public/js* directory.

3.- Include *public/js/jekyll-search.js* in the default template.

```html
<!-- scripts -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
<script src="{{site.baseurl}}/public/js/jquery.fitvids.js"></script>
<script src="{{site.baseurl}}/public/js/jekyll-search.js"></script>
```
4.- Initiaize SimpleJekyllSearch in the default layout.

```html
<!-- scripts -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
<script src="{{site.baseurl}}/public/js/jquery.fitvids.js"></script>
<script src="{{site.baseurl}}/public/js/jekyll-search.js"></script>
<script type="text/javascript">
SimpleJekyllSearch.init({
    searchInput: document.getElementById('search-input'),
    resultsContainer: document.getElementById('results-container'),
    dataSource: '{{ site.baseurl }}/search.json',
    searchResultTemplate: '<li><a href="{url}" title="{desc}">{title}</a></li>',
    noResultsText: 'No results found',
    limit: 10,
    fuzzy: false,
  })
</script>
```

5.- Style the search input. I have added the next code in my *public/css/main.scss* file.

```css
#search-input {
  display: inline-block;
  padding: .5em;
  width:100%;
  font-size: 0.8em;
  box-size: border-box;
}
```
