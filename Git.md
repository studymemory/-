# Git
<!-- GFM-TOC -->

* [GIt](#git)
  * [集中式与分布式](#集中式与分布式)

  * [中心服务器](#中心服务器)

  * [工作流](#工作流)

  * [分支实现](#分支实现)

  * [冲突](#冲突)

  * [Fast forward](#fast forward)

  * [储藏(Stashing)](#储藏stashing)

  * [SSH传输设置](#SSH传输设置)

  * [.gitignore文件](#gitignore文件)

  * [Git命令一览](#git-命令一览)

  * [参考资料](#参考资料)

	<!-- GFM-TOC -->

## 集中式与分布式

Git属于分布式版本控制系统，而SVN属于集中式
    
<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208200656794.png"/> </div><br>


集中式版本控制系统只有中心服务器拥有一份代码，而分布式版本控制系统每个人的电脑就有一份完整的代码。
	
集中式版本控制系统有安全性问题，当中心服务器挂了所有人都没办法工作了
	
集中式版本控制系统需要联网擦能工作，如果网速过慢，那么提交一个文件都会慢的让人无法接受，而分布式版本控制系统不需要联网就能工作。
分布式版本控制系统新建分支、合并分支操作速度非常快，而集中式版本控制系统新建一个分支相当于复制一份完整代码。
## 中心服务器
中心服务器用来交换每个用户的修改，没有中心服务器也能工作，但是中心服务器能够24小时保持开机状态，这样就能更方便的交换修改。
Github就是一个中心服务器
## 工作流
新建一个仓库之后，当前目录就成了工作区，工作区有一个隐藏目录.git,它属于Git的版本库

Git的版本库有一个称为Stage的暂存区以及最后的额History版本库，History存储所有的分支信息，使用一个HEAD指针指向当前分支

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208195941661.png"/> </div><br>

- git add files把文件的修改添加到暂存区
- git commit把暂存区的修改提交到当前分支，提交之后暂存区就被清空了
- git reset --files使用当前分支上的修改覆盖暂存区，用来撤销最后一次git add files;
- git checkout --files使用暂存区的修改覆盖工作目录，用来撤销本地修改

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208200014395.png"/> </div><br>

可以跳过暂存区直接从分支中取出修改，或者直接提交修改到分支中。

- git commit -a直接把所有的文件的修改添加到暂存区然后执行提交
- git checkout HEAD -- files

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208200543923.png"/> </div><br>

## 分支实现

使用指针 将每个提交连接成一条时间线，HEAD指针指向当前分支指针

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208203219927.png"/> </div><br>

新建分支是新建一个指针指向时间线的最后一个节点，并让 HEAD 指针指向新分支，表示新分支成为当前分支。

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208203142527.png"/> </div><br>

每次提交只会让当前分支指针向前移动，而其它分支指针不会移动。

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208203112400.png"/> </div><br>

合并分支也只需要改变指针即可。

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208203010540.png"/> </div><br>

## 冲突

当两个分支都对同一个文件的同一行进行了修改，在分支合并时就会产生冲突。
<div align="center"><img src="https://cs-notes-1256109796.cos.apguangzhou.myqcloud.com/image-2019120191208203034705.png"/></div><br>

Git会使用<<<<，=====，>>>>标记出不同分支的内容，只需要把不同分支中冲突部分修改成一样就能解决冲突

```
<<<<<<< HEAD
Creating a new branch is quick & simple.
=======
Creating a new branch is quick AND simple.
>>>>>>> feature1
```
## Fast forward

“快进式合并”（fast-forward merge）,会直接将master分支指向合并的分支，这种模式下进行分支合并会丢失分支信息，也就不能在分支历史上看出分支信息

可以在合并时加上--no-ff参数来禁用Fast forward模式，并且加上-m参数让合并时产生一个新的commit.

```
$ git merge --no-ff -m "merge with no-off" dev

```
<div align="center"><img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/image-20191208203639712.png"/> </div><br>

## 储藏

在一个分支上操作之后，如果还没有将修改提交到分支上，此时进行切换分支，那么另一个分支上也能看到新的修改，这是因为所有分支都共用一个工作区的缘故。

可以使用git stash将当前分支的修改储藏起来，此时当前工作区的所有修改都会被存到栈内，
也就是说当前工作区是干净的，没有任何未提交的修改，此时就可以安全的切换的到其他分支上了。

```
$ git stash
Saved working directory and index state \ "WIP" on master:049d087 added the index file"
HEAD is now at 049d087 added the index file (To restore them type "git stash apply")
```
该功能可以用于bug分支的实现，如果当前正在dev分支上进行开发，但是此时master上有个bug需要修复，但是dev分支上的开发还未完成，不想立即提交，在新建bug分支并切换到bug分支之前就需要使用git stash将dev 分支的未提交修改储藏起来。。
## SSH传输设置

Git仓库和Github中心仓库之间的传输是通过SSH加密。

如果工作区下没有ssh目录，或者该目录下没有id_rsa和id_rsa.pub这两个文件，可以通过以下命令来创建SSH Key：

```
$ ssh-keygen -t rsa -C "youremail@example.com"
```
然后把公钥id_rsa.pub的内容复制到Github"Accout settings"的SSH Keys中。

## .gitignore 文件

忽略以下文件：

- 操作系统自动生成的文件，比如缩略图；
- 编译生成的中间文件，比如 Java 编译产生的 .class 文件；
- 自己的敏感信息，比如存放口令的配置文件。

不需要全部自己编写，可以到 [https://github.com/github/gitignore](https://github.com/github/gitignore) 中进行查询。

## Git 命令一览

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/7a29acce-f243-4914-9f00-f2988c528412.jpg" width=""> </div><br>

比较详细的地址：http://www.cheat-sheets.org/saved-copy/git-cheat-sheet.pdf

## 参考资料

- [Git - 简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)
- [图解 Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)
- [廖雪峰 : Git 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [Learn Git Branching](https://learngitbranching.js.org/)