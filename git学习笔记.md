# GIT 

Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。

本章将对有关创建与提交你的项目快照的命令作介绍。

Git 常用的是以下 6 个命令：

**git clone**、**git push**、**git add** 、**git commit**、**git checkout**、**git pull**

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：或本地仓库
- remote repository：远程仓库

## Git 工作流程

- 克隆 Git 资源作为工作目录。

- 在克隆的资源上添加或修改文件。

- 如果其他人修改了，你可以更新资源。

- 在提交前查看修改。

- 提交修改。

- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

  ![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

## git 工作区、暂存区和版本库

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫 stage area 或 index。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库：**工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库。
- ![img](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)



**创建仓库**

* git init  初始化仓库
* git clone 拷贝一份远程仓库

**提交与修改**

* git add 添加文件到仓库
* git status 查看仓库当前的状态，显示有变更的文件。
* git diff 比较文件的butong，暂存区和工作区的差异。
* git commit 提交暂存区到本地仓库
* git reset 回退版本
* git rm 删除工作区文件
* git mv 移动或重命名工作区文件。

**提交日志**

* git log  查看历史提交记录
* git blame <file> 以列表形式查看指定文件的历史修改记录

**远程操作**

| 命令         | 说明               |
| :----------- | :----------------- |
| `git remote` | 远程仓库操作       |
| `git fetch`  | 从远程获取代码库   |
| `git pull`   | 下载远程代码并合并 |
| `git push`   | 上传远程代码并合并 |

## Git mv 命令

git mv 命令用于移动或重命名一个文件、目录或软连接。

```
git mv [file] [newfile]
```

如果新但文件名已经存在，但还是要重命名它，可以使用 **-f** 参数：

```
git mv -f [file] [newfile]
```

我们可以添加一个 README 文件（如果没有的话）：

```
$ git add README 
```

然后对其重命名:

```
$ git mv README  README.md
$ ls
README.md
```

## 忽略文件

添加需要忽略的文件名到 .gitignore 文件中 如果没有.gitignore 需要添加一个



```
git ls-files
```

 ``` 
git rm --catched -r directory/
 ```



## Git status short

git status -s 命令返回的提交情况相对更简洁明了

？？添加

M 修改

A 已添加

## DIFF

git diff 命令比较文件的不同，即比较暂存区和工作去差异。

git diff 命令显示已写入暂存区和已经被修改但尚未写入暂存区文件对区别。

git diff 有两个主要的应用场景。

- 尚未缓存的改动：**git diff**
- 查看已缓存的改动： **git diff --cached**
- 查看已缓存的与未缓存的所有改动：**git diff HEAD**
- 显示摘要而非整个 diff：**git diff --stat**

git diff 配置为vscode

```
[user]
        name = wping
        email = 18204980702@163.com
[core]
        editor = vim
        auotocrlf = true
        autocrlf = false
[color]
        ui = true
[filter "lfs"]
        process = git-lfs filter-process
        required = true
        clean = git-lfs clean -- %f
        smudge = git-lfs smudge -- %f
[diff]
        tool = vscode
[difftool "vscode"]
        cmd = "code --wait --diff $LOCAL $REMOTE"
```

命令行输入 git difftool 

显示暂存区和工作区的差异:

```
$ git diff [file]
```

显示暂存区和上一次提交(commit)的差异:

```
$ git diff --cached [file]
或
$ git diff --staged [file]
```

显示两次提交之间的差异:

```
$ git diff [first-branch]...[second-branch]
```



## Viewing the History

git log  查看历史提交记录

git log --oneline  以行显示

git log --oneline --reverse  反序

## Viewing a Commit

git show



## Unstaging Files（取消暂存）

git status -s

git restore --staged 

## Discarding Local Changes

git restore .

git clean