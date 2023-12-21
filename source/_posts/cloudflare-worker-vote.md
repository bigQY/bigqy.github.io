---
title: 使用cloudflare的worker搭建一个投票系统
---

# 效果演示

## 投票
![投票结果](https://vote.zzdx.gay/api/vote/15/result.svg)
### 投票选项
[选项A](https://vote.zzdx.gay/api/vote/15/voteUrl?optionId=55)
[选项B](https://vote.zzdx.gay/api/vote/15/voteUrl?optionId=56)

# 搭建过程

## 创建项目

创建一个文件夹，用来存储项目，文件夹名称随意，不要含有中文或者特殊符号

## 配置wrangler

进入创建的项目目录，执行命令
```bash
npm install wrangler --save-dev
```
或者
```bash
yarn add --dev wrangler
```

## 复制代码

