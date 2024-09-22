---
title: Creating a Blog using GitHub as a CMS
date: Sat Sep 21, 2024
---
This post is to demonstrate using GitHub as a CMS to serve markdown.
<!-- end -->
  This post’s content and metadata are stored in a single Markdown file accessible on a public GitHub [repository](https://github.com/dvh-sh/blog). 

  When a user loads the `/blog` route or any blog post (`/blog/[id]`), the client sends a request to the GitHub API; Then, using `gray-matter` and `react-markdown`, the content, date, title, and excerpt are parsed, and the content is displayed.
  
  However, one disadvantage of using GitHub as a CMS is the rate limiting. 
