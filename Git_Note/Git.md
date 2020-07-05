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