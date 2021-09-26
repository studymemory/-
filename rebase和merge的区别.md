# rebase
本地的两个分支，一个我的分支test一个主分支master
现在我修改的部分要合并到master上，可以有两种选择merge和rebase，两者的最后得到的结果是一样的，但是区别是rebase一个两个分支，就各位了一个分支，test合并前所有的patch也就是commit消失了。
而merge则还是两个分支，只不过在merge后这个点交汇
# merge

# rebase
为了让分支树看起来更加简化，我们选择rebase如何rebase呢？首先我的本地代码库不是最新的，所以先从远端resposity拉一下pull
```
git checkout master
git pull 
```
然后开始用 test合并rebase

```
git checkout test
git rebase master
```
这个时候就可以rebase 了，一般情况下rebase都是含有冲突的，详细查看冲突可以用命令git status然后就会显示哪个文件有冲突，然后打开有冲突的文件，会发现有一些：“<<<<"","====="",">>>>>

git add -u
git rebase ---continue
继续后才会出现第二个冲突，知道所有的冲突解决完，而Merge是所有冲突都会显示出来，如果
rebase过程中，你想中途退出，恢复rebase前的代码则可以用命令
```
git rebase --abort 
```
所以rebase 的工作流是




最后PR(pull request)
rebase工作流
```
git rebase
while(存在冲突）

```

merge工作流
```
git pull (或fetch&&merge)
git pull


```
变基和直接合并
