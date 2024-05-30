---
title: "Static Blog"
date: 2023-05-31 06:00:00 +0800
last_modified_at: 2023-05-31 12:00:00 +0800
categories: [blog]
tags: [learning, blog, code]
---

## Set Up 

To begin my coding journey, I wanted to create a blog so as to keep track of my progress. After much deliberation, I decided to use Jekyll as it was the simplest to get it up and running.

Jekyll will directly create a static page that can be deployed onto Github Pages with a subdomain of our username.

I followed a tutorial by [Ahmed Tremo](https://www.youtube.com/@ahmedtremo) for the setup process:

{% include /embed/youtube.html id="m1RYsmOMPLs" %}

## Running Local Server

```bash
bundle exec jekyll s
```

> This command is used to set up a local server to preview the blog first before plublishing which is very useful.
{: .prompt-tip }

## Useful Syntax 

I also found some websites which has useful syntax for Jekyll markdown:

1. [Jekyll Markdown Cheat Sheet](https://www.ihsantopaloglu.com/Jekyll-Markdown-Cheat-Sheet/) by ihsantopaloglu
2. [Basic Syntax](https://www.markdownguide.org/basic-syntax/) by MarkDownGuide
3. [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#GitHub-flavored-markdown) by Github

## Special Blocks 

> This is an example of a Tip.
{: .prompt-tip }

> This is an example of an Info block.
{: .prompt-info }

> This is an example of a Warning block.
{: .prompt-warning }

> This is an example of a Danger block.
{: .prompt-danger }

```md
> This is an example of a Tip.
{: .prompt-tip }

> This is an example of an Info block.
{: .prompt-info }

> This is an example of a Warning block.
{: .prompt-warning }

> This is an example of a Danger block.
{: .prompt-danger }
```