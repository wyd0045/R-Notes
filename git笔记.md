# 核心概念

![图片1](IMG/git笔记/git-command.jpg)

- 空间

  - workspace 工作区
  - staging area 暂存区
  - local repository本地仓库
  - remote repository 远程仓库
- 文件状态

  - Untracked 未跟踪

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

## 创建本地仓库

- 创建 git 仓库

  ```shell
  git init
  ```
  
  ## 连接远程仓库
  
  - 将本地仓库连接到远程仓库
  
  ```shell
  git remote add <shortname> <URL>
  ```
  
  `<shortname>` 为连接名，`<URL>` 为远程仓库地址，远程仓库地址可以是 HTTPS URL 也可以是 SSH URL. 

## 查看

- 查看仓库当前状态

  ```shell
  git status
  ```

  显示的内容有：

  - 当前所处的分支
  - 处于各状态的文件

- 查看历史提交记录

  ```shell
  git log # 只展示当前所在分支上的所有提交
  ```

  ```shell
  git log --all # 以逆时间序展示本地仓库中所有分支的提交
  ```

- 查看分支

  ```shell
  git branch # 查看本地分支
  ```

  ```shell
  git branch --all # 查看本地分支和远程跟踪分支
  ```

- 查看当前仓库所有已跟踪文件

  ```shell
  git ls-files
  ```

- 查看远程仓库和本地仓库的区别

  ```shell
  git diff <branch1> # 查看分支 <branch1> 与当前分支的区别
  ```

  ```shell
  git diff <branch1> <branch2> # 查看分支 <branch1> 和 <branch2> 的区别
  ```

  `<branch1>` 和 `<branch1>` 均可以是远程跟踪分支。

- 查看本地仓库到远程仓库的连接

  ```shell
  git remote # 查看本地仓库到远程仓库所有连接的连接名
  ```

  ```shell
  git remote -v # 查看本地仓库到远程仓库所有连接的连接名和 URL
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

- 将本地仓库的代码推送到远程仓库

  ```shell
  git push <shortname> <branch_name>
  ```

  ```shell
  git push -u <shortname> <branch_name> # 推送并设定上游分支
  ```


​	`<shortname>` 为连接名，`<branch_name>` 为本地分支名。

- 从远程仓库下载一个项目

  ```shell
  git clone
  ```

- 将远程仓库提取到本地仓库

  ```shell
  git fetch # 创建或更新所有已连接的远程仓库的所有分支的远程跟踪分支
  ```

  ```shell
  git fetch origin main # 创建或更新仓库 origin 的分支 main 的远程跟踪分支 origin/main
  ```

- 将远程仓库拉取到本地工作区

  ```shell
  git pull
  ```

  `git pull` 命令的效果相当于 `git fetch` 加上 `git merge`.  

- 将文件从暂存区或工作区中删除

  ```shell
  git rm newfile.txt # 删除 newfile.txt，并将该文件从暂存区中移除（该删除操作会被放入暂存区中，等待下一次提交）
  ```

  ```shell
  git rm --cached newfile.txt # 仅从暂存区中移除文件，但不进行实际的物理删除，而是将该文件修改为 Untracked 状态（该删除操作会被放入暂存区中，等待下一次提交）
  ```

  ```shell
  git rm -r newfolder # 递归删除 newfolder文件夹下的所有文件，并将该文件夹从暂存区中移除（该删除操作会被放入暂存区中，等待下一次提交）
  ```

- 恢复或撤销文件的更改

  ```shell
  git restore # Git 2.23 版本引入
  ```

## 分支管理

- 新建分支

  ```shell
  git branch bad-boy # 新建名为 bad-boy 的新分支
  ```

- 切换分支

  ```shell
  git switch bad-boy # 切换到名为 bad-boy 的分支（Git 2.23 版本引入）
  ```

  ```shell
  git switch -c bad-boy # 创建并切换到名为 bad-boy 的分支（Git 2.23 版本引入）
  ```

  ```shell
  git checkout bad-boy # 切换到名为 bad-boy 的分支
  ```

  ```shell
  git checkout -b bad-boy # 创建并切换到名为 bad-boy 的分支
  ```

  ```shell
  git checkout 09cf587 # 切换到 Hash 值为 09cf587 的提交
  ```

  切换分支时，Git 会用该分支最后一次提交的内容替换工作目录中的当前内容， 所以多个分支不需要多个目录。

  检出提交（checkout commit）时会进入 detached HEAD 状态，不推荐。

- 创建并切换到新分支

  ```shell
  git checkout -b temp # 创建并切换到名为 temp 的新分支
  ```

  ```shell
  git checkout -b totallyNotMain o/main # 创建并切换到名为 totallyNotMain 的新分支，使该分支跟踪远程分支 o/main
  ```

- 删除分支

  ```shell
  git branch -d bad-boy # 删除名为 bad-boy 的分支（如果有未提交的更改 git 会拒绝删除）
  ```

  ```shell
  git branch -D bad-boy # 强制删除未合并的分支 bad-boy
  ```

- 合并分支

  ```shell
  git merge <branch1> # 将分支 <branch1> 合并到当前分支
  ```

  ```shell
  git merge –-continue # 解决合并冲突后，继续合并操作
  ```
  
  `<branch1>` 可以是本地分支，也可以是远程跟踪分支。

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

- 查看目录的文件结构

  ```shell
  tree .git/refs # 查看目录 .git/refs 的文件结构
  ```

## vim 编辑器

- `i` （insert）进入编辑状态
- **ESC** 退出编辑状态
- `:wq` 保存并退出编辑器
- `:w` （write）保存文件
- `:q` （quit）退出编辑器
- `:x` 文件有修改时与 `:wq` 相同，文件没有修改时直接退出，不进行保存操作。

# 在 Pycharm 中使用 Git

## 准备工作

1. 在 Pycharm 中关联本地 git.exe，具体操作为

# 深入理解

- 分支

  分支是指向提交（commit）的可移动指针。.git/refs/heads文件夹中的每一个文件表示一个本地分支，其内容是该分支最新一次提交（commit）的 Hash 值。

- HEAD

  HEAD 是指向当前所在分支的指针，可通过 `git log` 或 `git branch` 查看。查看 .git 文件夹中的 HEAD 文件可以看到，文件内容如下。

  ```
  ref: refs/heads/main
  ```

- 切换分支时，git 都做了哪些事？
  1. 将 HEAD 指向目标分支。
  2. 使用和目标分支相对应的提交快照填充暂存区。
  3. 将暂存区内容拷贝到工作目录。

- 合并

  将一个分支集成到另外一个分支的两种方式：

  1. 合并（merge）
  2. 变基（rebase）

  合并的两种方式：

  1. 快进合并（fast-forward merge）
  2. 三方合并（three-way merge）

  快进合并和三方合并的区别是，快进合并中源分支和目标分支其中一个是另一个的祖先，而三方合并则是两者有一个共同的祖先。

- 远程仓库

  本地仓库和远程仓库之间相互独立，两者的交互不会自动发生。

  远程仓库按照惯例应该命名为 origin，一个本地仓库理论上可以有多个到远程仓库的连接，但不常见。

- 远程分支

  本地分支：在本地仓库中的分支。

  远程分支：在远程仓库中的分支。

  远程跟踪分支（remote-tracking branch）：在本地仓库中的对远程分支所指向的提交（commit）的一个引用。

  上游分支（upstream branch）：本地分支指向的远程分支。上游分支可以和其对应的本地分支不同名，但通常应该保持同名。

  在使用 `git pull/push` 命令时，如果上游分支已经设定，则不需要添加额外的参数。

- 在执行 `git push` 命令时，git 都做了哪些事？

  1. 在远程仓库中创建或更新对应的远程分支。
  2. 在本地仓库中创建或更新对应的远程跟踪分支。

- 在执行 `git fetch` 命令时，git 都做了哪些事？

  1. 查询当前连接的所有远程仓库。
  2. 创建或更新所有已连接的远程仓库的所有分支对应的本地远程跟踪分支。

  （ `git fetch` 命令可以指定想要创建或更新本地远程跟踪分支的远程仓库及分支）

# 问题

1. rebase（变基）和merge（合并）有什么区别？

   Merge 和 Rebase 是 Git 中常用的两种分支整合方式，它们具有不同的工作原理和效果。

   合并是将两个或多个分支的提交历史合并为一个新的提交。在合并时，Git 会创建一个新的合并提交，将两个分支的修改合并在一起。合并提交将包含两个分支的修改，并且保留了每个分支的提交历史。合并通常用于将一个分支中的修改合并到另一个分支中，或者合并不同开发人员的工作。

2. git 的用户体系是怎样的？

   git 本地似乎没有用户体系可言，只需要设置一个用户名和邮箱即可。权限校验都在连接远程仓库时进行。

   ```shell
   fatal: detected dubious ownership in repository at 'C:/Users/Administrator/Desktop/R-Notes'
   'C:/Users/Administrator/Desktop/R-Notes' is owned by:
           BUILTIN/Administrators (S-1-5-32-544)
   but the current user is:
           DESKTOP-QLP9SPN/Administrator (S-1-5-21-1101309422-1141911820-4091053739-500)
   To add an exception for this directory, call:
   
           git config --global --add safe.directory C:/Users/Administrator/Desktop/R-Notes
   ```

   以上报错的原因是当前文件夹属于的用户与当前终端登录的用户不同，与 git 用户体系无关。解决方法：右键单击文件夹，在属性 -> 安全 -> 高级 -> 所有者中将所有者修改为当前终端登录的用户（即 ESKTOP-QLP9SPN/Administrator）即可。

3. GitHub 仓库的默认分支（default branch）有什么用？

   执行 `git clone` 命令时，下载的是该仓库的默认分支。

4. 设置执行 `git push` 命令不指定任何参数时的默认行为

   ```shell
   git config --global push.default <value>
   ```

   其中 `<value>` 的值可以为：

   - nothing

     必须显示指定想要推送到的远程分支，否则会拒绝 push 操作。

   - matching

     表示向所有与本地分支同名的远程分支推送。

   - current

     表示将当前分支推送到与其名称相同的远程分支。

   - upstream

     表示将当前分支推送到其上游分支。

   - simple

     simple 的效果与 upstream 相似，只是 simple 必须保证当前分支与其上游分支同名，否则会拒绝 push 操作。

   在 Git 2.0 之前的版本中，`<value>` 的默认值为 matching，在 Git 2.0 之后的版本中，`<value>` 默认值为 simple. 

# 参考网站

[Bilibili：Git工作流和核心原理 | GitHub基本操作 | VS Code里使用Git和关联GitHub](https://www.bilibili.com/video/BV1r3411F7kn/?spm_id_from=333.880.my_history.page.click&vd_source=b3328ecaea4c890b0870cbe5c6c5e30c)

[菜鸟教程：Git 教程](https://www.runoob.com/git/git-basic-operations.html)

[CSDN：小工具推荐：FastGithub的下载及使用](https://blog.csdn.net/qq_43554335/article/details/134066165)

[简书：总结 下git rm --cached,git rm -r ,git -r --cached 三者的区别和容易混淆的地方](https://www.jianshu.com/p/39ed531505a3)

[CSDN：Git查看本地分支和远程分支之间的关系](https://blog.csdn.net/weixin_51480428/article/details/141015661)

[阿里云：细读 Git | 让你弄懂 origin、HEAD、FETCH_HEAD 相关内容](https://developer.aliyun.com/article/919354)

[CSDN：git config --global push.default simple 的相关解读](https://blog.csdn.net/myself88129/article/details/132605504)

