# Git用法指南

## Git的三个存储区

### 1. 工作区(Working Directory/Tree)

本地文件目录就是工作区，修改直接写入到文件

### 2. 暂存区(Stage or Index)

通过`git add`命令可以将文件添加到暂存区，而命令`git commit`就是把暂存区的的数据提交到的版本库。因此暂存区是工作区和版本库之间的数据传输的中间层。

### 3. 版本库(Commit History)

`git commit`后数据被提交到版本库，版本库里面保存了所有提交的历史信息

### 如何实现不同区的数据传输

最基本的就是`git add`和`git commit`，除此之外常用命令还有：

1. `git checkout <file>`：将指定的文件从暂存区复制到工作区
2. `git reset [--mixed] [<commit>]`：回退到指定的提交，并将文件从版本库复制到暂存区
3. `git reset --soft [<commit>]`：仅回退到指定的提交，文件不做改变
4. `git reset --hard [<commit>]`：回退到指定提交，并将文件从版本库复制到暂存区和工作区

## Git中的分支(Branch)

分支可以很方便让多人对同一个项目进行互不干预的开发，也可以实现版本管理，在必要的时候能够通过合并分支来实现项目整合。

分支的一个重要属性是指向它最后一次提交的指针。一个特殊的分支是HEAD分支，始终表示当前分支。

### 创建分支

命令：`git branch <branch-name>`

基于当前分支，创建一个新的分支

### 查看分支

命令：`git branch [<opotion>]`

### 删除分支

命令：`git branch -d <branch-name>`

### 合并分支

命令：`git merge <branch-name>`
将指定的分支合并到当前分支。分支的合并分两种情况：

#### 1. 快进式(Fast-Forward)

当两个分支存在上下游关系的时候，采用快进式合并分支方法，这时候需要做的仅仅是指针的移动

#### 2. 策略合并式(Recursive Strategy Merge)

当两个分支不存在上下游关系时，分支的合并采取的策略是将两个分支的数据合并后作为新的提交，然后将合并后的分支指向该提交。注意这里的数据合并可能存在冲突，所以有时候需要手动修改冲突，然后提交。

如果想要强行指定用策略合并的方式可以加上`no-off`参数。

## Git工作流

顾名思义工作流表示工作的流程，也被称为分支管理策略，目前最受欢迎的工作流是以下三种：

1. Git Flow
2. GitHub Flow
3. GitLab Flow

### Git Flow规则

#### 主要分支

1. master：永远是版本发布状态
2. develoop：永远是最新的开发进度

#### 协助分支

1. Feature Branch：具体开发某个功能模块的分支
2. Release Branch：版本预发布的分支，可以在这个分支做测试和问题修改
3. Hotfix Branch：用来做线上的紧急bug修复，命名建议hotfix-xxx

#### Git Flow示意图

![Git Flow示意图](../res/img/git-flow.png)

## 其他命令

1. `git stash`：将当前**工作区和暂存区**的改动保存，回到没有任何改动的提交。
2. `git stash pop [--index]`：将之前stash保存的数据恢复到**工作区**，如果加上`--index`选项则恢复到**工作区和暂存区**
3. `git revert [<commit>]`：逆转指定提交，即新增的数据删除，删除的数据新增，然后将逆转后的数据作为一次新的提交
