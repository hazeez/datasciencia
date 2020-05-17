---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}

# post thumb - set only one image
#image: "images/featured-post/post-1.jpg"
image: "images/post/post-3.jpg"

# meta description
description: "this is meta description"

# taxonomies
categories: 
  - "Cat1"
tags:
  - "tag1"
  - "tag2"

# post type - 'featured' or 'post'
#type: "featured"

# set the slug for the post
slug: "test-slug"

# keywords
keywords:
- technology

# comments - set to 'true' or 'false'
comments: false

showMeta: false
showActions: false

# draft post or not - set 'true' or 'false'
draft: true
---

