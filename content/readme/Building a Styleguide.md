---
title: "Building a Style guide"
date: 2021-01-06T18:22:00+02:00
draft: true
---
## The goal with the style guide
* Documentation of components and guidelines.

## Content of the style guide


### Simple page
A documentation page.
Requires:
* markdown-file (.md)

### Component
Requires:
* markdown-file (.md)
* template file (.mustache)
* data file (.json)

### Page template
* Do Not have a .md file
* Do have a .mustache file.

The style guide will look at the url; `https://styleguide:3000/components/my-object`then check if a .md file exist there `/project/components/my-object/my-object.md`if it doesn't try to find a file with that name so if the url is `https://styleguide:3000/components/my-object/my-object.html`.

It is possible in Node to watch for file/directory changes.
https://davidwalsh.name/node-watch-file