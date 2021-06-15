---
title: My Hexo Setting
categories: hexo
tags: hexo
keywords: hexo
description: this blog's hexo setting
abbrlink: 30609
date: 2021-06-14 23:19:40
---



### [Hexo](https://hexo.io/)

**Required**: nodejs and npm

```bash
npm install hexo-cli -g
```

<!-- more -->

Uexo Command Usage

```
Usage: hexo <command>

Commands:
  clean     Remove generated files and cache.
  config    Get or set configurations.
  deploy    Deploy your website.
  generate  Generate static files.
  help      Get help on a command.
  init      Create a new Hexo folder.
  list      List the information of the site
  migrate   Migrate your site from other system to Hexo.
  new       Create a new post.
  publish   Moves a draft post from _drafts to _posts folder.
  render    Render files with renderer plugins.
  server    Start the server.
  version   Display version information.

```



### Page - Markdown

[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

```bash
# Add tags, categories, and about pages
hexo new page tags
hexo new page categories
hexo new page about

# New a post
hexo new "Post Name"
```

Post Header

```markdown
title: My Hexo Note
date: 2021-06-12 01:53:11
categories: hexo
tags: hexo

<!-- more -->
```



### [Hexo Theme - NexT](https://github.com/theme-next/hexo-theme-next)

```bash
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

#### NexT Config - `themes/next/_config.yml`

```yaml
minify: true
pjax: true
scheme: Gemini
darkmode: auto

copy_button:
	enable: true
  # Show text copy result.
	show_result: true
  # Available values: default | flat | mac
  style: mac

mediumzoom: true

busuanzi_count:
  enable: false
  enable: true
```

#### Google Analytics

```yaml
google_analytics:
  tracking_id: # <app_id>
```

#### Disqus Comment

Login and Setup a Disqus Account: https://disqus.com/

```yaml
# Disqus
disqus:
  enable: true
  shortname: ranger-chans-blog
```



### [Hexo Plugins](https://hexo.io/plugins/)

#### [GitHub Deployer](https://github.com/hexojs/hexo-deployer-git)

```bash
npm install hexo-deployer-git --save
```

`_config.yml`

```yaml
url: https://rangerz.github.io/blog

# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repo: git@github.com:rangerz/blog.git
  branch: github-pages
  message: Update blog at {{ now('YYYY-MM-DD HH:mm:ss') }}
```

- Deploy GitHub Command

```bash
hexo deploy
```



#### [Sitemap](https://github.com/hexojs/hexo-generator-sitemap)

```bash
npm install hexo-generator-sitemap --save
```

`_config.yml`

```yaml
sitemap:
   path: sitemap.xml
```



#### [RSS Feed](https://github.com/hexojs/hexo-generator-feed)

```bash
npm install hexo-generator-feed --save
```

`_config.yml`

```yaml
# RSS Feed
## Docs: https://github.com/hexojs/hexo-generator-feed
feed:
  enable: true
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon: icon.png
  autodiscovery: true
  template:
```

`themes/next/_config.yml`

```yaml
rss: /atom.xml
```

`themes/next/layout/_partials/sidebar/site-overview.swig`

```html
{% if theme.rss %}
  <div class="feed-link motion-element">
    <a href="{{ url_for(theme.rss) }}" rel="alternate">
      <i class="fa fa-rss"></i>
      RSS
    </a>
  </div>
{% endif %}
```



#### [nofollow](https://github.com/liuzc/hexo-autonofollow)

```bash
npm install hexo-autonofollow --save
```

`_config.yml`

```yaml
nofollow:
  enable: true
```



#### [lazyload-image](https://github.com/Troy-Yang/hexo-lazyload-image)

```bash
npm install hexo-lazyload-image --save
```

`_config.yaml`

```yaml
lazyload:
  enable: true
  onlypost: false
```



#### Google Search

https://search.google.com/search-console/welcome

Input URL Prefix: https://rangerz.github.io/blog/

HTML Tag: `<meta name="google-site-verification" content="aODVh6Swyz72uqikurLQBpNIqJO68gqxnPpEc2Pm9kI" />`

Add to `themes/next/layout/_partials/head/head.swig`



#### [permalink](https://github.com/rozbo/hexo-abbrlink)

```bash
npm install hexo-abbrlink --save
```

`_config.yaml`

```yaml
permalink: posts/:abbrlink/

abbrlink:
  alg: crc32
  rep: hex
```



#### [Search DB](https://github.com/theme-next/hexo-generator-searchdb)

```bash
npm install hexo-generator-searchdb --save
```

`_config.yaml`

```yaml
search:
  path: search.xml
  field: post
  content: true
  format: html
```

`themes/next/_config.yml`

```yaml
local_search:
  enable: true
```



#### robots.txt

Add file: `source/robots.txt`

```yaml
# robots.txt for https://rangerz.github.io/blog/

User-agent: *

Allow: /
Allow: /about/
Allow: /archives/
Allow: /categories/
Allow: /tags/

Disallow: /images/
Disallow: /js/
Disallow: /css/
Disallow: /lib/

Sitemap: https://rangerz.github.io/blog/search.xml
Sitemap: https://rangerz.github.io/blog/sitemap.xml
```





