---
title: "Learning Vue.js"
date: 31/5/2024 22:45:00
last_modified_at: 31/5/2024 22:14:00
categories: [vuejs]
tags: [learning, blog, code]
---

## Introduction
I am learning Vue.js for the purpose of creating a project where students learn about flowcharts, you can see my progress on this here.

It is a bit hard, learning Vue.js while still not understanding most of js, but I think it will be faster this way. I followed a [video series](https://www.youtube.com/playlist?list=PL4cUxeGkcC9hYYGbV60Vq3IXYNfDk8At1){:target="_blank"} by Net Ninja who has a whole tutorial on Vue.js.

{% include /embed/youtube.html id="YrxBCBibVo0" %}

## What is Vue.js?

From what I could understand, Vue.js is essentially a way for programmers to dynamically render their site. To do so, Vue.js either inject the code into the site as an app, or the entire site would just be the app. This would allow for various components to be instantly displayed and run by Vue.js rather than waiting for a response from the server every time the user clicks on a link.


## Starting Off
As a beginner, Net Ninja recommended using the CDN first to implement Vue.js into our site. With a standard html document, reference the script like this into our header.

``` html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

And then create a `app.js` in our project and then reference it.

Then to inject vue from our js file into our site, we should first create a div which we will inject our app into which is as simple as creating a div with an id of <span style="color:dodgerblue"> ‘app’</span>.

``` html
<div id="app"></div>
```

Then in our `app.js`, we create a new Vueapp through the function of `Vue.createApp()` before mounting the app into our div with the id of <span style="color:dodgerblue">‘app’</span>.

``` js
const app = Vue.createApp()

app.mount("#app")
```

Now let’s talk about template, template is basically just the html code we want inside our app. (I believe). Anyways, we can go about adding templates into our app through two ways. One is by writing it in our `Vue.createApp()` function or directly inside our <span style="color:dodgerblue">‘app’</span> div.

For example

``` html
<div id="app">
	<p>Hello World!</p>
</div>
```
or
``` js
const app = Vue.createApp({
	Template: '<p>Hello World!</p>'
})

app.mount("#app")
```
