# Git

## git配置全局用户名

git——git bash

```git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

## git简易使用

### 创建版本库

git bash here

```git
$ git init
```

### 添加文件

```git
$ git add <filename>
$ git add --all  //添加目录下的所有文件
```

### 提交文件

```git
$ git commit -m "message"
```

* **提交之后返回改动**

## 历次版本

### 修改和状态的查看

```Git
$ git status
$ git diff <filename>
```

* git status 查看是否修改和是否提交，管理仓库的状态.
* git diff 查看修改的内容（增删）

### 版本回退

#### 版本日志查看

```git
$ git log
```

* git log 会按提交时间列出所有的更新，最近的更新排在最上面。每次更新都有一个 SHA-1 校验和、作者的名字 和 电子邮件地址、提交时间，最后缩进一个段落显示提交说明。
* 简化输出参数  --pretty=oneline
* `log -1`表示最后一次提交
* [git log的详细操作](https://www.jianshu.com/p/0805b5d5d893)。

#### 回退操作

```git
$ git reset --hard HEAD
```

* 在Git中，用`HEAD`表示当前版本，也就是最新的提交，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

#### 恢复操作

* 在命令窗口没有被关闭的前提下，找到之前的版本号(commit id)

  `$ git reset --hard commit_id`

* `$ git reflog` 查看历史

### 工作区和暂存区

* git添加文件进入版本库

1. `git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

2. 是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，在未有其他分支情况下`git commit`就是往`master`分支上提交更改。可以简单理解为，需要提交的文件修改通通放到暂存区，然后一次性提交暂存区的所有修改。

### 管理、撤销修改

#### 管理修改

`$ git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面最新版本的区别

每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中。

* 修改一次，add一次
* 两次合并之后最后add、commit

#### 撤销修改

`git checkout -- <filename>`

* 撤销工作区的所有修改

1. 自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

2. 已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。

* `git checkout -- file`命令中的`--`很重要，没有`--`，就变成了“切换到另一个分支”的命令

`git reset HEAD <file>`

* 可撤销暂存区的修改（unstage），重新放回工作区

### 删除文件

`rm <filename>`

* 删除文件夹中的(工作区)文件

`git rm <filename>`

`git commit -m  "message"`

* 从版本库中删除该文件

`git checkout -- <filename>`

* `git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。###

## 远程仓库

#### 添加远程仓库

```git
$ git remote add origin git-账户名称
```

* 关联远程仓库

```git
$ git push -u origin master
```

* 将本地文件推送到远端  //第一次

* ```git
  $ git push origin master //之后的
  ```

* 删除远程仓库

  `$ git remote rm origin`  //或者在gitconfg内删除[temote "origin"] 内容

#### 远程克隆

```git
$ git clone <address>
```

* Git支持多种协议，包括`https`，但`ssh`协议速度最快。

## 分支管理

### 创建合并分支

* 指针指向的变化

1. master指向提交
2. HEAD指向当前分支
3. 工作区文件指向HEAD

* 新分支的产生

1. HEAD指向新分支
2. 新分支指向提交

#### 创建分支

```git
$ git checkout -b <name>
```

* `git checkout`命令加上`-b`参数表示创建并切换，相当于以下两条命令：

```git
$ git branch <name>
$ git checkout <name>
```

或者使用switch命令

```git
$ git switch -c <name>  //创建并切换
$ git switch master  //切换
```

#### 查看当前分支

```git
$ git branch
```

* `git branch`命令会列出所有分支，当前分支前面会标一个`*`号。

```git
$ git checkout master
```

* 切换分支

#### 合并分支

```git
$ git merge <name>
```

* 将分支name合并到当前的分支

#### 删除分支

```git
$ git branch -d <name>
```

* **合并分支之后，一般都会删除分支** 

### 解决冲突

* `git status`可以告诉我们冲突的文件
* Git用`<<<<<<<`，`=======`，`>>>>>>>`标记出不同分支的内容
* 分支修改为相同内容

```git
$ git log --graph --pretty=oneline --abbrev-commit
```

* 用带参数的`git log`可以看到分支的合并情况
* `git log --graph`命令可以看到分支合并图

### 分支策略管理

通常，合并分支时，如果可能，Git会用`Fast forward`模式，但这种模式下，删除分支后，会丢掉分支信息。

如果要强制禁用`Fast forward`模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

```git
$ git merge --no-ff -m "merge with no-ff" name
```

* `--no-ff`参数，表示禁用`Fast forward`

1. 主分支稳定，用来发布新版本
2. 其他分支完成工作

### Bug分支

#### 临时储存

```git
$ git stash
```

* 把当前工作现场“储藏”起来，等以后恢复现场后继续工作

```git
$ git stash list
```

* 工作现场还在，Git把stash内容存在某个地方，查看stash列表

#### 恢复

```git
$ git stash pop
```

* 恢复的同时把stash内容也删了

`$ git stash apply`

* 恢复内容后，stash内容并不删除

`$ git stash drop`

* 删除stash内容

恢复指定的stash内容

```git
$ git stash apply stash@{0}  //stash列表序号
```

#### bug处理

```git
$ git checkout <name>    //确定bug出现的分支
$ git checkout -b <name>  //在bug出现的分支下进行分支
```

* 两个分支上相同bug的处理

```git
$ git cherry-pick <commit>
```

* 在提交一次之后，转到另外一个分支，pick相同的commit_id

### Feature分支

类似于bug分支，带有新功能实验性质

在分支未被合并时，需要强行删除，将删除分支命令中的`-d`改为`-D`即可：

```git
$ git branch -D <name>
```

### 多人协作

当你从远程仓库克隆时，实际上Git自动把本地的`master`分支和远程的`master`分支对应起来了，并且，远程仓库的默认名称是`origin`。

#### 查看远程库的信息

`$ git remote`
`$ git remote -v  //显示更详细的信息 显示了可以抓取和推送的`origin`的地址。如果没有推送权限，就看不到push的地址`

#### 推送分支

```git
$ git push origin <branch-name>
```

但是，并不是一定要把本地分支往远程推送:

- `master`分支是主分支，因此要时刻与远程同步；
- `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

#### 抓取分支

从远程库clone时，默认情况下，只能看到本地的`master`分支，可以用`git branch`命令查看。

要在`dev`分支上开发，就必须创建远程`origin`的`dev`分支到本地；

```git
$ git checkout -b dev origin/dev  //创建dev分支并且与远程库的dev分支关联起来
```

修改完进行提交推送时发生冲突，先用`git pull`把最新的提交从`origin/dev`抓下来，然后，在本地合并，解决冲突，再推送。

* 需要指定本地分支与远程`origin`分支的链接，否则容易`pull`错误 (`no tracking information`)

* ```git
  $ git branch --set-upstream-to <branch-name> origin/<branch-name>
  ```

##### git fetch / git pull

`git fetch`是将远程主机的最新内容拉到本地，便于进行自动合并工作本机分支中。

`git pull` 则是将远程主机的最新内容拉下来后直接合并，即：`git pull = git fetch + git merge`，这样可能会产生冲突，需要手动解决。

* 相对来说 git fetch更安全一点
* 详情参见 [git fetch / git pull详解](https://www.cnblogs.com/runnerjack/p/9342362.html)

### Rebase

多人在同一个分支上协作时，很容易出现冲突。即使没有冲突，后push的童鞋不得不先pull，在本地合并，然后才能push成功。

```git
$ git rebase
```

- rebase操作可以把本地未push的分叉提交历史整理成直线，缺点是本地的分叉提交已经被修改。
- rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

## 标签管理

Git的标签虽然是版本库的快照，但其实它就是指向某个commit的指针（跟分支很像对不对？但是分支可以移动，标签不能移动），所以，创建和删除标签都是瞬间完成的。

### 创建标签

```git
$ git tag <name> commit_id
```

* 创建一个新标签
* 默认标签是打在最新提交的commit上的，如果忘了打标签，找到历史提交的commit id，然后打上就可以了

```git
$ git tag
```

* 查看所有标签

```git
$ git show <tagname>
```

* 查看标签信息

```git
$ git tag -a <tagname> -m "message" commit_id
```

* 创建带有说明的标签，用`-a`指定标签名，`-m`指定说明文字

**标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签。**

### 操作标签

1. 删除标签

```git
$ git tag -d <tagname>
```

* **因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。**

2. 推送标签到远程

```git
$ git push origin <tagname>
```

3. 一次性推送全部尚未推送到远程的本地标签

```git
$ git push origin --tags
```

4. 删除远程的标签

* 先从本地删除

```git
$ git tag -d <tagname>
```

* 从远程删除

```git
$ git push origin :refs/tags/<tagname>
```

## Git配置

* git显色明显

```git
$ git config --global color.ui true
```

### 忽略文件配置

在Git工作区的根目录下创建一个特殊的`.gitignore`文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。

* 被`.gitignore`忽略的文件的强行添加

```git
$ git add -f <filename>  // -f = --force  表示强制完成
```

* `.gitignore`书写错误的检查

```git
$ git check-ignore -v <filename>
```

Git会告诉我们，`.gitignore`的第几行规则忽略了该文件

- 忽略某些文件时，需要编写`.gitignore`；
- `.gitignore`文件本身要放到版本库里，并且可以对`.gitignore`做版本管理！
- 其他`.gitignore`的配置，详情请参见 [GitHub`.gitignore`配置](https://github.com/github/gitignore)

### 配置别名

例如 `st`就表示`status`

```git
$ git config --global alias.st status  // alias 表示别名
```

用`co`表示`checkout`，`ci`表示`commit`，`br`表示`branch`：

```git
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
```

* `--global`参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。

## 其余操作、知识

本文均来自于[廖雪峰Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)。





最近发现git更新了许多东西，详情参见官方文档。