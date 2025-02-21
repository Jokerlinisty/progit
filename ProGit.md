# 第一章 Git基础

## Git项目初始化 

git init

## 克隆现有仓库 

git clone https://github.com/libgit2/libgit2

## Git文件状态

- 已跟踪：已纳入git版本管理
- 未跟踪：未纳入git版本管理

## Git文件状态转换

【未跟踪】 git add【已暂存】 

- git reset head / git restore --staged【未跟踪】

- git commit 【已提交未修改】

【已提交未修改】modify【已修改】

- git add 【已暂存】
- git checkout / git restore 【已提交未修改】

【已提交未修改】remove【未跟踪】

## 查看文件状态

git status

## 跟踪新文件（将文件添加到下次提交中）

git add

## 忽略文件

.gitignore

## 提交更新

git commit

## 移除文件（不再跟踪文件）

git rm

## 查看提交历史

git log

## 撤销操作

git commit --amend

## 取消暂存文件

git reset HEAD

git restore

## 撤销对文件的修改

git checkout

git restore

## 查看远程仓库

git remote -v

## 添加远程仓库

git remote add https://github.com/paulboone/ticgit 

## 从远程仓库抓取

git fetch

## 从远程仓库拉取（抓取并尝试自动合并）

git pull







