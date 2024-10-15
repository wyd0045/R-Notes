# 核心原理

![图片1](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

- 空间

  - workspace 工作区
  - staging area 暂存区
  - local repository本地仓库
  - remote repository 远程仓库

- 文件状态

  - Untracked/Unstage 未跟踪

    新创建的文件最初是未跟踪的。它们存在于工作目录中，但没有被 Git 跟踪。

  - Tracked 已跟踪

    通过 `git add` 命令将未跟踪的文件添加到暂存区后，文件变为已跟踪状态。

  - Modified 已修改

    对已追踪的文件进行更改后，这些更改会显示为已修改状态，但这些更改还未添加到暂存区

  - Staged 已暂存

    使用 `git add` 命令将修改过的文件添加到暂存区后，文件进入已暂存状态，等待提交。

  - Commited 已提交

    使用 `git commit` 命令将暂存区的更改提交到本地仓库后，这些更改被记录下来，文件状态返回为已跟踪状态。

- 操作

  - add
  - commit
  - push
  - fetch/clone
  - checkout
  - pull

# 实操

## 设置用户名和邮箱

- 查看当前用户

  ```shell
  git config --global --list
  ```

- 设置用户名

  ```shell
  git config --global user.name "王一丁"
  ```

- 设置邮箱

  ```shell
  git config --global user.email "717086377@qq.com"
  ```

## 创建 Git 仓库

- 创建 git 仓库

  ```shell
  git init
  ```

## 查看当前状态

- 查看仓库当前状态

  ```shell
  git status
  ```

  显示的内容有：

  - 当前所处的分支
  - 处于各状态的文件

-  查看历史提交记录

  ```shell
  git log
  ```

- 查看当前仓库所有已跟踪文件

  ```shell
  git ls-files
  ```

- 查看当前本地仓库和哪些远程仓库有联系

  ```shell
  git remote -v
  ```

  默认使用 `origin` 表示远程仓库，在 push 的时候可以使用 `origin` 代替远程仓库的 URL. 

- 查看远程仓库和本地仓库的区别

  ```shell
  git diff origin/main # 查看名为 origin 的远程仓库的 main 分支与本地仓库当前分支的区别
  ```

## 主要操作

- 将文件添加到暂存区

  ```shell
  git add lao.md
  ```

- 提交暂存区到本地仓库。

  ```shell
  git commit
  ```

  ```shell
  git commit -m "Commit message" # 将 Commit message 作为提交信息 
  ```

  ```shell
  git commit -a # 将工作区的文件添加到暂存区并直接提交到本地仓库
  ```

  ```shell
  git commit -am "Commit message" # 将工作区的文件添加到暂存区并直接提交到本地仓库，同时将 Commit message 作为提交信息
  ```

-  将文件从暂存区和工作区中删除

  ```shell
  git rm newfile.txt # 删除指定的文件，并将其添加到暂存区，等待下一次提交
  ```

  ```shell
  git rm --cached newfile.txt # 仅从仓库中移除文件，但不进行实际的物理删除
  ```

- 从远程仓库下载一个项目

  ```shell
  git clone
  ```

- 将远程仓库更新到本地仓库

  ```shell
  git fetch
  ```

- 将本地仓库的代码推送到远程仓库

  ```shell
  git push
  ```

- 将远程仓库的代码合并到本地工作区

  ```shell
  git pull
  ```

## 分支管理

- 新建分支

  ```shell
  git branch bad-boy # 新建名为 bad-boy 的新分支
  ```

- 切换分支

  ```shell
  git checkout bad-boy # 切换到名为 bad-boy 的分支
  ```

  切换分支时，Git 会用该分支最后一次提交的内容替换工作目录中的当前内容， 所以多个分支不需要多个目录。

- 创建并切换到新分支

  ```shell
  git checkout -b temp # 创建并切换到名为 temp 的新分支
  ```

- 删除分支

  ```shell
  git branch -d bad-boy # 删除名为 bad-boy 的分支
  ```

  ```shell
  git branch -D bad-boy # 删除未合并的分支 bad-boy
  ```

- 将别的分支合并到当前分支

  ```shell
  git merge temp # 将名为 temp 的分支合并到当前分支
  ```

## 其他

- 创建文件夹

  ```shell
  mkdir my-project
  ```

- 进入文件夹

  ```shell
  cd my-project
  ```

- 创建文件

  ```shell
  echo "版本1" > lao.md # 创建一个新文件并写入“版本1”
  ```

  ```shell
  touch newfile.txt  # 创建一个新文件
  ```

- 清空命令行

  ```shell
  clear
  ```

- 使用 vim 编辑器编辑文件

  ```shell
  vim newfile.txt
  ```

## vim 编辑器

- `i` （insert）进入编辑状态
- **ESC** 退出编辑状态
- `:wq` 保存并退出编辑器
- `:w` （write）保存文件
- `:q` （quit）退出编辑器

# 在 Pycharm 中使用 Git

## 准备工作

1. 在 Pycharm 中关联本地 git.exe，具体操作为

# 问题

1. rebase（变基）和merge（合并）有什么区别？

   Merge 和 Rebase 是 Git 中常用的两种分支整合方式，它们具有不同的工作原理和效果。

   合并是将两个或多个分支的提交历史合并为一个新的提交。在合并时，Git 会创建一个新的合并提交，将两个分支的修改合并在一起。合并提交将包含两个分支的修改，并且保留了每个分支的提交历史。合并通常用于将一个分支中的修改合并到另一个分支中，或者合并不同开发人员的工作。
   
2. git 的用户体系是怎样的？

# 参考网站

[Bilibili：Git工作流和核心原理 | GitHub基本操作 | VS Code里使用Git和关联GitHub](https://www.bilibili.com/video/BV1r3411F7kn/?spm_id_from=333.880.my_history.page.click&vd_source=b3328ecaea4c890b0870cbe5c6c5e30c)

[菜鸟教程：Git 教程](https://www.runoob.com/git/git-basic-operations.html)

[CSDN：小工具推荐：FastGithub的下载及使用](https://blog.csdn.net/qq_43554335/article/details/134066165)
