## 工作流程及原理

### Git 的工作流程：

![图 1](../../images/7b13efaa8b23ca4527650c3cd24755bc5cfb91fa6244d1f5c392a3c5cc8f68b6.png)

- workspace(工作区):
  本地电脑存放项目文件的地方，我们平时开发写的代码也是在这个区进行的；
- Index / Stage(暂存区):
  暂时存放文件的地方，通过 add 命令可以将工作区的文件添加到暂存区内；
- Repository(本地仓库):
  .git 文件夹里还包括 git 自动创建的 master 分支，并且将 HEAD 指针指向 master 分支。使用 commit 命令可以将暂存区中的文件添加到本地仓库中；
- Remote(远程仓库):
  项目代码在远程 git 服务器上，通常使用 clone 命令将远程仓库拷贝到本地仓库中，开发后通过 push 推送到远程仓库中；

![图 2](../../images/f8602d137ea8f1c4b9f5d094ffb0f5952eb038236ea368c9b2402e08801e538d.png)

## Git 基本操作

### git add

添加文件到暂存区

```bash
# 添加某个文件到暂存区，后面可以跟多个文件，以空格区分
git add xxx
# 添加当前更改的所有文件到暂存区。
git add .
```

### git commit

```bash
# 提交暂存的更改，会新开编辑器进行编辑
git commit
# 提交暂存的更改，并记录下备注
git commit -m "you message"
# 等同于 git add . && git commit -m
git commit -am
# 对最近一次的提交的信息进行修改,此操作会修改commit的hash值
git commit --amend

```

### 撤销

```bash
# 恢复暂存区的指定文件到工作区
git restore --staged [file]  # 2.23.0 引入了一个新命令，基本上是git reset的替代方案
git reset HEAD [file]
#$ git checkout [file] # ???貌似失效了

# 恢复工作区的指定文件，与上一次commit保持一致
git restore [file]


# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

# 恢复暂存区的所有文件到工作区
$ git checkout .

# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]

# 暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop
```

### 远程同步

```bash
##### pull
# 从远程仓库拉取代码并合并到本地，可简写为 git pull 等同于 git fetch && git merge
git pull <远程主机名> <远程分支名>:<本地分支名>
# 使用rebase的模式进行合并
git pull --rebase <远程主机名> <远程分支名>:<本地分支名>

##### fetch
# git fetch：与 git pull 不同的是: git fetch **仅仅只会拉取远程的更改，不会自动进行 merge 操作。对你当前的代码没有影响**
# 获取远程仓库特定分支的更新
git fetch <远程主机名> <分支名>
# 获取远程仓库所有分支的更新
git fetch --all

##### push
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
# 推送所有分支到远程仓库
$ git push [remote] --all

##### 显示
# 显示所有远程仓库
$ git remote -v
# 显示某个远程仓库的信息
$ git remote show [remote]

##### 增加
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
```

### 分支

```bash
##### 增
# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
# 新建一个分支，并切换到该分支
$ git checkout -b [branch-name]
# 新建一个分支，指向指定commit
$ git branch [branch-name] [commit]
# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch-name] [remote-branch]

##### 删
# 删除本地分支
git branch -d <branch-name>
git branch -D <branch-name> #强制删除

##### 改
# 重新命名分支
git branch -m <old-branch-name> <new-branch-name>

##### 查
# 查看本地分支
git branch
# 查看远程分支
git branch -r
# 查看本地和远程分支
git branch -a

##### 合并
# 合并指定分支到当前分支
$ git merge [branch]
# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

##### 切换
# 切换到指定分支，并更新工作区
$ git checkout [branch-name]
# 切换到上一个分支
$ git checkout -

##### 远程操作
# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]


```

## 工作中使用 Git 解决问题的场景

### git rebase 让提交记录更加清晰可读

#### 修改 提交的信息

```bash
# -i：interaction
git rebase -i [要修改提交信息的commit的父级commit hash]
#r, reword <提交> = 使用提交，但编辑提交说明
```

#### 合并 连续的 commit

```bash
# -i：interaction
git rebase -i [要合并的最早commit的父级commit hash]

# 将 ddc9654 合并到 cc33542
pick cc33542 add 4.js
s ddc9654 rebase: 4.js #s, squash <提交> = 使用提交，但挤压到前一个提交

```

#### 合并 间隔的 commit

```bash
###### 将 commit 5 合并到 commit 1
# commit 5 (hash5)
# commit 4 (hash4)
# commit 3 (hash3)
# commit 2 (hash2)
# commit 1 (hash1)
git rebase -i [hash1]
# 将 commit 5 合并到 commit 1
pick hash1 commit 1
s    hash5 commit 5   #s, squash <提交> = 使用提交，但挤压到前一个提交
pick hash4 commit 4
pick hash3 commit 3
pick hash2 commit 2

#
git rebase --skip

```

![图 4](../../images/8d19c93a93f305d5abfcc5e954655aa67a3c48fe8609e03f3da95ae3943da69a.png)

![图 5](../../images/f52e26646dbd836bf078e16f761a607bcf2cccf3a187621dd28fe00338cd6a63.png)

rebase(变基)，作用和 merge 很相似，用于把一个分支的修改合并到当前分支上。

如下图所示，下图介绍了经过 rebase 后提交历史的变化情况。

![图 3](../../images/70aa7f8f89b0b144161798228ba7eb0db3add74cc2d747e893a34f88cee0f97d.png)

###

###

###

###

## 参考资料

- [常用 Git 命令清单](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
- [我在工作中是如何使用 git 的](https://juejin.cn/post/6974184935804534815#heading-20)

- [all-about-git](https://gitee.com/all-about-git)
- [Git 常用命令总结](https://www.freecodecamp.org/chinese/news/collection-of-useful-git-commands/)
- [一份前端老菜鸟的 Git 总结](https://juejin.cn/post/7028459321667092488)
