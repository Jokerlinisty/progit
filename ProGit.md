# 第一章 Git基础

## Git保存原理

Git是直接记录所有文件快照，而不是每次文件的改动，所以Git每次提交都会产生一个新的快照（文件校验和）

## Git项目初始化 

git init

## 克隆现有仓库 

git clone https://github.com/libgit2/libgit2

## Git文件状态

- 已跟踪：已纳入git版本管理
- 未跟踪：未纳入git版本管理

## Git文件状态流转

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

git remote show origin

## 添加远程仓库

git remote add https://github.com/paulboone/ticgit 

## 从远程仓库抓取

git fetch

## 从远程仓库拉取（抓取并尝试自动合并）

git pull

## 推送到远程仓库

git push

## 打标签

git tag -a v1.0 -m '1.0'

## 删除标签

git tag -d v1.0

## 推送标签

git push origin --tags

# 第二章 Git分支

## 每次提交一个文件包含三个对象

- 一个blob文件对象（保存文件快照）
- 一个树对象（记录文件目录结构及blob文件对象索引）
- 一个提交对象（记录指向树对象的指针、提交信息（作者等）及上次提交对象的指针）

## 创建分支

git branch 分支名称

此时会在当前提交对象上创建一个指针，指向当前提交对象

## 当前分支

HEAD指针指向的分支即当前分支

## 切换分支

git checkout 分支名称











