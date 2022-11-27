---
title: '[Hexo] Upgrade Note'
categories: hexo
tags: hexo
keywords: hexo
description: note for commands to upgrade hexo
abbrlink: 9e71c229
date: 2022-11-26 21:59:44
---



### Long Time No See

好久回來整理 blog 了, hexo 的 [dependabot](https://github.com/apps/dependabot) 一直發 [Pull requests](https://github.com/rangerz/blog/pulls) 通知我要更新 ... 真是好心, 一時間也不知道怎麼升級 npm 相關的 package, google 了一下寫點筆記, 下次回來還能用到



### 常用指令

先打個岔 寫一些常用指令

```bash
# Install hexo, required nodejs and npm
npm update hexo-cli -g

hexo init # 初始化環境
hexo n {$title} # 新增 post 會存在 source/_posts/
hexo clean # 清除 cache
hexo g -s # 安靜的 generate
hexo s # server, 本地測試
hexo d # deploy 會 git push 上去
```



### 升級指令

目標就是和 dependabot 的 PR 做一樣的事, 更新 `package.json` 和 `package-lock.json` 

```bash
# 升級 node 和 npm (Optional)
brew update node
npm update -g npm

# 確認 npm packages 版本
npm outdated

# 升級 hexo-cli
npm update -g hexo-cli
hexo version

# 更新全域的 npm packages (Optional)
npm update -g

# 安裝 npm-check 和 npm-upgrade
npm install -g npm-check npm-upgrade
npm-check && npm-upgrade

# 安裝新版 - 記得 push 新的 package.json 和 package-lock.json
npm install
git add package.json package-lock.json yarn.lock

# Theme 更新 - 記得設定檔要留下來
git clone https://github.com/theme-next/hexo-theme-next themes/next

# 發布
hexo clean
hexo g -s
hexo d
```
