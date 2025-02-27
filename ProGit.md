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

git fetch 实际上将本地仓库中的远程分支更新成了远程仓库相应分支最新的状态

git fetch 并不会改变你本地仓库的状态。它不会更新你的 `main` 分支，也不会修改你磁盘上的文件

## 从远程仓库拉取（抓取+合并）

git pull = git fetch + git merge

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

此时会在当前提交对象上创建一个指针，指向当前提交对象以

Git分支本质上只是一个包含所指向提交对象校验和（长度为40的SHA-1值字符串）  的文件，所以创建和销毁都非常高效

创建一个新分支相当于往一个文件里写入41 个字节（40 个字符和 1 个换行符）  

## 当前分支

HEAD指针指向的分支即当前分支

## 切换分支

git checkout 分支名称

## 合并分支

git merge 分支名称

## 快速合并

快进（fast-forward）  ： 如果将当前分支合并到当前提交对象的**直接上游**提交对象对应的分支，则Git只是将目标分支指向当前提交对象

比如将develop合并到master，则只是将master分支指向develop分支指向的提交对象，此时不会产生新的提交对象

## 三方合并

如果目标分支的提交对象并不是当前分支提交对象的**直接上游**，那么Git无法执行快速合并，而是会执行**三方合并**

三方合并即将两个分支指向的最新快照和二者最近的共同祖先进行三方合并

三方合并后，Git会创建一个新的提交对象（合并提交），此时当前提交对象有两个父提交对象

## 合并方式

当远程分支中有新的提交时，你可以像合并本地分支那样来合并远程分支

- git merge origin/main
- git rebase origin/main
- git cherry-pick origin/main

## 分支开发工作流

## 主分支

master

## 特性分支

feature/xxx

## 远程分支

origin/xxx

本地存储的指向的远程提交对象的分支，可能落后于最新的远程分支（指向最新的提交对象）

可以通过git fetch更新远程仓库信息（包含远程已更新，但本地还没有的数据，如分支、tag等）

## 跟踪分支

从一个远程跟踪分支检出一个本地分支会自动创建所谓的 “跟踪分支”  

跟踪分支是与远程分支有直接关系的本地分支

如果在一个跟踪分支上输入git pull, Git能自动地识别去哪个服务器上抓取、合并到哪个分支  

## 删除远程分支

git push origin --delete 远程分支名称

## 变基

Git整合不同分支有两种方式：合并（merge）和变基（rebase）

变基即将某一分支的提交修改一个一个的移到另一个分支上

变基的原理是先找到两个分支的最近共同祖先，然后将当前分支相当于该祖先分支的每个提交的修改保存为一个个临时文件，然后按顺序将保存的临时文件基于目标分支逐个还原提交

## 变基的风险

不要对在你的仓库外有副本的分支执行变基 

只要你把变基命令当作是在推送前清理提交使之整洁的工具，并且只在从未推送至共用仓库的提交上执行变基命
令，就不会有事

假如在那些已经被推送至共用仓库的提交上执行变基命令，并因此丢弃了一些别人的开发所
基于的提交，那你就有大麻烦了，你的同事也会因此鄙视你 

总的原则是，只对尚未推送或分享给别人的本地修改执行变基操作清理历史，从不对已推送至别处的提交执行变
基操作  

# 第三章 服务器上的Git

# 第四章 分布式Git





