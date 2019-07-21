# The Jekyll Template for Cotes' Blog

[![Build Status](https://travis-ci.org/cotes2020/cotes-blog.svg?branch=master)](https://travis-ci.org/cotes2020/cotes-blog)
[![GitHub release](https://img.shields.io/github/release/cotes2020/cotes-blog.svg)](https://github.com/cotes2020/cotes-blog/releases)
[![GitHub license](https://img.shields.io/github/license/cotes2020/cotes-blog.svg)](https://github.com/cotes2020/cotes-blog/blob/master/LICENSE)
[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)

My personal Jekyll blog, please check the deployment: [https://blog.cotes.info](https://blog.cotes.info).

## Configuration

Check files in `_data/`, they are:

* meta.yml
* profile.yml
* settins.yml

Open, and override the fields inside to your own.


## Writing

There are some things you must know about writing a post:

### TOC

The [Front Matter](https://jekyllrb.com/docs/front-matter/) `toc` in posts is to decide whether to display the **Table of Content** or not, default to `ture`, select `false` to disable.

### Comments

The field `comments` is the switch for **Disqus** comment module, the default value is `true`, to disable it select `false`.

>You have to configurate the **Disqus** in file `_data/meta.yml`, override the field `disqus-shortname`.

### Categories And Tags

The pages for posts' categories and tags are placed in the `categoreis/` and `tags/` respectively.

Let's say there is a post with title `The Beautify Rose`, it's Front Matter as follow:

```
---
title: "The Beautify Rose"
categories: [Plant]
tags: [flower]

 ...

---
```

Then you need to create two new files for `categories` and `tags`:

1.Create **category** file `categories/Plant.html` and fill:

```yaml
---
layout: category
title: Plant        # The title of category page.
category: Plant     # The category name in post
---
```


2.Create **tag** file `tags/flower.html` and fill:

```yaml
---
layout: tag
title: Flower       # The title of tag page.
tag: flower         # The tag name in post.
---
```

If you find this to be time consuming, please use the script tool `pages_generator.py`.

The python script needs [ruamel.yaml](https://pypi.org/project/ruamel.yaml/), make sure it's installed in your environment, then run the script:

```bash
python _scripts/tools/pages_generator.py
```

Few seconds later, it will create the Categoreis and Tags HTML files automatically.

## Deployment

First run requires the following command:

```bash
bundle install
```

`bundle` will install all plugins declared by `Gemfile` automatically.

### Local

```bash
bundle exec jekyll serve
```

Open your brower and visit: [http://127.0.0.1:4000](http://127.0.0.1:4000)

### GitHub Pages

Step 1. Build project locally and output to folder `docs` in the root.

```bash
bundle exec jekyll build JEKYLL_ENV=production -d docs
```

Step 2. Commit and push the changes of `/docs` to remote repository.

Step 3. [Publishing your GitHub Pages site from a /docs folder on your master branch
](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch).
