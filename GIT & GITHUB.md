# GIT & GITHUB

## commit wording

PRESENT : FIX the bug

PAST: Fixed the bug

staging area 暂存区

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