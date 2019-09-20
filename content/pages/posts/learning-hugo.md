---
title: "Learning Hugo"
date: 2019-09-15T15:36:10+01:00
draft: false
author: "Rosana Rufer"
---

Hugo's static site generator has a very good quick start section that got me up and running with the basic structure but I soon wanted to go a bit further forward and the documentation wasn't very much adapted to my needs, so I'm taking a few notes about the most important concepts from my point of view:

To start I would split these core concepts into **content** as information structure, and **theme** as styling the structure because I want to have my theme to match my current website style.

## Content

### Content types

1. Single Pages: Just a page that displays information. 
2. List Pages: Pages that list other pages.

When you build your website you want to break your content into single pages and list pages.

### Content data

**Frontmatter** is any set of metadata that defines data values

```
name = "my name"
date: 2017012 ...

```
Provided using [front-matter](https://gohugo.io/content-management/front-matter/) you can choose any format.

You can create your custom frontmatter variables


**Archetypes**: They define the default values that are assigned to a newly created template. The default frontmatter values for **any** new content are defined in the `default.md` file.

For any directory inside `content` an `archetype can be added to define the default values specific to that directory.

**Shortcodes**

Hugo-specific tags that can be used to render different types of content. Such as `hilight`:

<p>`{{< highlight go >}} A bunch of code here {{< /highlight >}}`
</p>
Will render as:

{{< highlight go >}} A bunch of code here {{< /highlight >}}



