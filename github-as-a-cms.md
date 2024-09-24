---
title: Creating a Blog using GitHub as a CMS
date: Sat Sep 21, 2024
---
This post is to demonstrate using GitHub as a content management system (CMS) to serve markdown.
<!-- end -->
  This post’s content and metadata are stored in a single Markdown file accessible on a public GitHub [repository](https://github.com/dvh-sh/blog). 

  When a user loads the `/blog` route or any blog post (`/blog/[slug]`), the client sends a request to the GitHub API; Then, using `gray-matter` and `react-markdown`, the content, date, title, and excerpt are parsed, and the content is displayed.
  
  However, one disadvantage of using GitHub as a CMS is the [rate-limiting](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api?apiVersion=2022-11-28). The GitHub API sets the primary rate-limit for unauthenticated requests to 60 per hour.

  For view counters, this blog utilizes [MongoDB Atlas](https://www.mongodb.com/atlas), which provides a free tier with up to 500MB of storage. The server employs `mongoose` to define a basic schema comprising two properties: *slug* and *views*. Upon loading the `/blog` route, all view counts are indexed. Conversely, when the `/blog/[slug]` route is accessed, an individual blog post document is indexed by  *slug*. If the document exists, the counter is incremented. If the document is absent, the same function used to increment blog posts’ views also creates a new document within the database.
