# kxhh's blog

> > Welcome to kxhh's blog! Here, let's explore uncharted territory together, including cryptocurrencies, technology, science, culture, products, big events, artificial intelligence, travel, food, and more. My goal is to provide readers with interesting, useful, and inspiring content, self-growth, and opening new horizons together.

## About page

The content of the about page is in the `source/about/index.md` file, which you need to modify.

## Add new article

> Once saved here, it will be posted to the website, so it is recommended to upload it after mdnice has written it.

1. Create a new `markdown` file in the `source/_posts` directory with a name in the format of `title.md`, e.g. `hello-world.md` or `hello-world.md`. 2.
2. Add the following to the header of the `markdown` file:

```md
---
title: 标题
date: 发布时间（格式：2023-07-17 20:00:00）
categories:
  - 类别
tags:
  - 标签1
  - 标签2
description: 描述
cover: 封面图片（可选，没有请删掉这一行）
---
```

## Add a new link

In the `source/_data/link.yml` file, follow the format to add a new link.

## Site information modification

If you are not satisfied with the site information generated by default, you can change it in the `config.yml` file:

```yml
title: kxhh's blog
subtitle: Explore uncharted territories and open new horizons
description: Welcome to kxhh's blog! Here, let's explore uncharted territory together, including cryptocurrencies, technology, science, culture, products, big events, artificial intelligence, travel, food, and more. My goal is to provide readers with interesting, useful, and inspiring content, self-growth, and opening new horizons together.
keywords:
# Author name, which is displayed in the sidebar
author: 
```

The description of the sidebar author information field can be modified in the `_config.butterfly.yml` file:

```yml
card_author:
  description: Explore uncharted territories and open new horizons
```

Announcements can also be modified in the `_config.butterfly.yml` file：

```yml
card_announcement:
  content: A simple and elegant blog
```

Social information changes are also made in the `_config.butterfly.yml` file：

```yml
social:
  fas fa-envelope: mailto:xxxxx@gmail.com || Email || '#4a7dbe'
  fab fa-twitter: https://twitter.com/xxxxx || Twitter || '#00acee'
```

## Changing images

The default header and cover images may not work for you, these are in the `_config.butterfly.yml` file:

```yml
# 首页 banner 图片
index_img: 

# 页面默认头图
default_top_img: 

# 归档页面默认头图
archive_img: 

# 标签页默认头图
tag_img: 

# 分类页默认头图
category_img: 

cover:
  # 文章页默认封面（随机）
  default_cover:
    - 
    - 
```

## Run locally

> > We recommend github for online editing, but if you're already using git, try running it locally.

```sh

$ git clone https://github.com/KXHH/www.cfra.top.git

$ yarn install

$ yarn server
```