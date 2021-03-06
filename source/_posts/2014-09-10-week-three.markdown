---
layout: post
title: 'Week 3: Introduction to JavaScript'
published: false
...

Quicksort implementation in JavaScript to illustrate recursion.

Notes for week three regarding using JavaScript to access an Omeka API.

Minimal HTML file loading D3 and

{% highlight html linenos %}

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <script src="http://d3js.org/d3.v3.min.js"></script>
  </head>
  <body>
    <script src="script.js"></script>
  </body>
</html>

{% endhighlight %}


Minimal JS

{% highlight javascript %}
var site = "http://americanconverts.org/api/site";

d3.json(site, ready);

var data;

function ready(response) {
  data = response;
  console.log(data);
}
{% endhighlight %}

Showing the images:

{% highlight javascript %}
var site = "http://americanconverts.org/api/site";
var items = "http://americanconverts.org/api/items?page=1";

d3.json(items, ready);

var data;

function ready(response) {
  data = response;
  console.log(data);
  for (var i = 0; i < data.length; i++) {
    d3.json(data[i].files.url, function(files) {
      for (var j = 0; j < files.length; j++) {
        var t = files[j].file_urls.thumbnail;
        console.log(t);
        document.write("<img src='" + t + "'/><br/>");
      }
    });
  }
}
{% endhighlight %}
