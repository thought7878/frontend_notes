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

## 参考资料

- [常用 Git 命令清单](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
- [all-about-git](https://gitee.com/all-about-git)
- [Git 常用命令总结](https://www.freecodecamp.org/chinese/news/collection-of-useful-git-commands/)
- [一份前端老菜鸟的 Git 总结](https://juejin.cn/post/7028459321667092488)
