---
title: "Learning the Basics of Vue.js"
date: 5/6/2024 13:30:00
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

## Data

Next is data or dynamic variables, this allows us to output variables that we can easily change. For that, we need to use the `data()` function inside our `Vue.createApp()`

``` js
const app = Vue.createApp({
    data() {
        return {
            counter: 15
        }
    }
})
```

And to reference it inside our app or template, we need to use curly brackets like this

``` html
<div id="app"> 
        Count: {% raw %} {{ counter }} {% endraw %}
</div>
```

Where we get something like this:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/data-01.png"></kbd>

## On-Click Event

We move on to click events where specific functions/methods will be carried out when these events are triggered.

The first one would be the `v-on:click` or we could also use @ to replace `v-on` as `@click` to listen for an event when the mouse clicks on the object/component

``` html
<button v-on:click="counter++">Increase count</button>
```

Then, we will get a result like this:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/click-01.gif"></kbd>

## Methods
We can run the codes inside our js component through the use of methods. For example, let’s say we want to create a method that changes a text from “Hello World” to “Hello Vue!”.

Firstly, let’s create our html code along with a button.

``` html
<div id="app"> 
        <h1> {% raw %} {{ text }} {% endraw %}</h1>

        <button v-on:click="changeText">Change text</button>
 </div>
```
Next, we will need to create a js script where we add a new component inside our app, that is the methods component and create a function called `changeText()`. This function will be invoked on the onclick event for the button. We need to add `this.` in front of our variable so as to be able to access it as it will reference the component itself, change the data.

``` js
const app = Vue.createApp({
    data() {
        return {
            text: "Hello World"
        }
    },
    methods: {
        changeText() {
            this.text = 'Hello Vue'
        }
    }
})
```

As a result, we get something like this:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/click-02.gif"></kbd>

At the same time, we are able to pass in a value into the function directly. For example:

``` html
<div id="app"> 
        <h1> {{ text }} </h1>

        <button v-on:click="changeText('Hello Vue')">Change text</button>
 </div>
```

``` js
const app = Vue.createApp({
    data() {
        return {
            text: "Hello World"
        }
    },
    methods: {
        changeText(text) {
            this.text = text
        }
    }
})
```
This will give us the same result as the function above, but we will be able to take in a argument and be able to change the value much more easily.

## Conditional Rendering

Vue allows for easy conditional rendering through the use of directives `v-if`, `v-else` and `v-show`. These will only show the content when it is true. This could be useful to create user login or a navbar dynamically.

Let’s create a block of text that will show and hide itself with a button.

``` html
<button @click="shownState = !shownState">
            <span v-if="shownState">Hide Text</span>
            <span v-else>Show Text</span>
</button>

<div v-show="shownState">
       	<h1> This is a text. </h1>
</div>
```

Along with a `shownState` variable to keep track of the state.

``` js
const app = Vue.createApp({
    data() {
        return {
            shownState: true
        }
    }
})
```

This will be the result:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/click-03.gif"></kbd>

However, you may be wondering what is the difference between `v-if` and `v-show`, if both of them will hide the text. This is because `v-if` directly removes the content from the html while `v-show` will use css to hide it. To use this effectively, `v-if` is better used in situations where things are rarely shown like user login state while `v-show` should be used in cases like navbars.

## Other Mouse Events

Other than the on-click event, there is also other events like:

1. `v-on:mouseover` where it is trigger when the mouse **enter** the component
2. `v-on:mouseleave` where it is trigger when the mouse **leaves** the component
3. `v-on:dblclick` where it is trigger when the mouse **double clicks** the component
4. `v-on:mousemove` where it is trigger when the mouse **moves inside** the component

At the same time, we can console log this event to receive useful properties like `ctrlKey` to know whether the control key was pressed or `type` to know the type of event.

``` html
<div v-on:mouseover="handleEvent($event)">mouseover</div>
```

```js
const app = Vue.createApp({
    methods: {
        handleEvent(e) {
            console.log(e, e.type)
        }
    }
})
```

We need to add a `$event` when we want to pass in our own arguments, but if we don’t pass any in, we will automatically get an event object as the first argument.

As another example, let’s make it so it will display the position of the mouse when it is inside a box using the `v-on:mouseover` event where it will constantly trigger an event handler that will update the position value.

``` html
<style>
        .box {
            padding: 100px 0;
            width: 400px;
            text-align: center;
            background: #ddd;
            margin: 20px;
            display: inline-block;
        }
  </style>
```

``` html
<div class="box" @mousemove="handleMousemove">position - {% raw %} {{ x }} - {{ y }} {% endraw %}</div>
```

``` js
const app = Vue.createApp({
    data() {
        return{
            x: 0,
            y: 0
        }
    },
    methods: {
        handleMousemove(e) {
            this.x = e.offsetX,
            this.y = e.offsetY
        }
    }
})
```

And this is the result:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/click-04.gif"></kbd>

## Using v-for to Output Lists

To create a list, we just need to use `[]` inside our data, for example:

``` js
const app = Vue.createApp({
    data() {
        return{
            books: [
                { title: 'One of Us is Lying', author: 'Karen McManus' },
                { title: 'All the Bright Places', author: 'Jennifer Niven' },
                { title: 'Holding Up the Universe', author: 'Jennifer Niven' }
            ]
        }
    }
})
```

We can easily access our list using indexes and calling the properties. For example: 

``` html
{% raw %} {{ books[0].title }} - {{ books[0].author }} {% endraw %}
```

We can also use `v-for` to loop over our list and create a component for each item in the list. 

``` html
<ul>
      <li v-for="item in books">
             <p>{% raw %} {{ item.title }} - {{ item.author }} {% endraw %}</p>
       </li>
</ul>
```
This would be our result:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/vfor-01.png"></kbd>

## Attribute Binding

If we want to reference a data property directly inside an attribute, we would need to use `v-bind:` or just a `:`. For example:

```js
const app = Vue.createApp({
    data() {
        return{
            url: "https://www.google.com"
        }
    }
})
```

``` html
<a href="url">Google</a>
```

If we reference our data property like this even if we add `{}`, it will fail like this: 

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/vbind-01.png"></kbd>

However, if we add `v-bind:` or `:` in front of the attribute, we will be able to reference the property.

``` html
<a v-bind:href="url">Google</a>
```

This time, we are successful:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/vbind-02.png"></kbd>

## Dynamic Classes

For dynamic classes, we will still need to use attribute binding but now we are able to dynamically add classes based on certain conditions for each object. For example, let’s say we want to add a `fav` class only when a property `isFav` is true.

``` js
const app = Vue.createApp({
    data() {
        return{
            books: [
                { title: 'One of Us is Lying', author: 'Karen McManus', img:"/assests/1.jpg", isFav: false },
                { title: 'All the Bright Places', author: 'Jennifer Niven', img:"/assests/2.jpg", isFav: true },
                { title: 'Holding Up the Universe', author: 'Jennifer Niven', img:"/assests/3.jpg", isFav: false }
            ]
        }
    }
})
```

``` html
<style>
        body {
            margin: 20px auto;
            max-width: 960px;
            background: #eee;
        }
        h1, p, ul {
            margin: 0;
            padding: 0;
        }
        img {
            width: 99px;
            height: 176px;
        }
        li {
            list-style-type: none;
            background: #fff;
            margin: 20px auto;
            padding: 10px 20px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        li.fav {
            background: #cc91e7;
            color:#fff;
        }
</style>
```

``` html
<ul>
       <li v-for="item in books" v-bind:class="{ fav: item.isFav }">
           <img v-bind:src="item.img" v-bind:alt="item.title">
           {% raw %}<h1>{{ item.title }}</h1>
           <p>{{ item.author }}</p>{% endraw %}
       </li>
</ul>
```
As you can see, we have a `v-bind:class` where we check if `isFav` is true, and add a `fav` class to it.

As a result:

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/vbind-03.png"></kbd>

For a bit of a challenge, let’s make it so that we can change `isFav` with a click of a button.

``` html
<ul>
    <li v-for="item in books" v-bind:class="{ fav: item.isFav }">
        <img v-bind:src="item.img" v-bind:alt="item.title">
        {% raw %}<h1>{{ item.title }}</h1>
        <p>{{ item.author }}</p>{% endraw %}
        <i @click=" item.isFav=!item.isFav " :class="{'fa-regular':!item.isFav, 'fa-solid':item.isFav }" class="fa-heart"></i>
    </li>
</ul>
```
When the heart is pressed, it will automatically change the class along with the `isFav` property.

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/vbind-04.gif"></kbd>

## Computed Properties

By using `computed`, we are able to compute some properties that we are able to retrieve through Vue.js.

For example, let’s say we want to compute a property where we filter the books array and get only books that return `isFav` as true. We can do this through the use of a filter method.

``` js
const app = Vue.createApp({
    data() {
        return{
            books: [
                { title: 'One of Us is Lying', author: 'Karen McManus', img:"/assests/1.jpg", isFav: false },
                { title: 'All the Bright Places', author: 'Jennifer Niven', img:"/assests/2.jpg", isFav: true },
                { title: 'Holding Up the Universe', author: 'Jennifer Niven', img:"/assests/3.jpg", isFav: true }
            ]
        }
    },
    computed: {
        filteredBooks() {
            return this.books.filter((book) => book.isFav)
        }
    }
})
```
And in our html code, we just need to change our mention of the books array

``` html
<ul>
    <li v-for="item in filteredBooks" v-bind:class="{ fav: item.isFav }">
        <img v-bind:src="item.img" v-bind:alt="item.title">
        {% raw %}<h1>{{ item.title }}</h1>
        <p>{{ item.author }}</p>{% endraw %}
        <i @click=" item.isFav=!item.isFav " :class="{'fa-regular':!item.isFav, 'fa-solid':item.isFav }" class="fa-heart"></i>
    </li>
</ul>
```

And just like that, we get only books that have the `isFav` as true.

<kbd><img src="/assets/img/posts/2024-05-31-learning-vuejs/computed-01.png"></kbd>

And that would be the basics of Vue.js, continue to my next post for my learnings of Vue.js CLI.
