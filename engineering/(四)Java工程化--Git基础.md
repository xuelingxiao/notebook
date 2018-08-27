# (四)Java工程化--Git基础

GIT学习参考：[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)

## 常见命令

* `git init` 初始化项目
* `git add *.java` 添加文件到git版本控制(.java后缀的全部文件)
<pre>
Git 有三种状态, commited(已提交),modified(已修改),staged(已暂存);已提交表示数据已经安全的保存在本地数据库中。 已修改表示修改了文件，但还没保存到数据库中。 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
由此引入 Git 项目的三个工作区域的概念：Git 仓库、工作目录以及暂存区域。
</pre>
* `git status -s` 当前状态,一般有进行下一步操作的提示信息 `-s`输出简洁信息
* `git commint -m '提交描述信息'` 提交到本地仓库
* `git clone https://github.com/xuelingxiao/java-knowledge-structure knstuct` 克隆远端仓库并重命名
        
        > GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表，你可以在 https://github.com/github/gitignore 找到它.
* `git diff` 查看哪些修改了还没有暂存；查看哪些修改暂存了准备下次提交；
* `git diff --cache` 查看暂存区
* `git commit -a` 跳过add,将跟踪文件暂存并一起提交
* `git rm filename.txt` 将文件移除跟踪状态
* `git rm --cached filename ` 从暂存区移除文件,将保留工作区文件
* `git mv filefrom fileto` 移动文件
* `git log` 查看提交历史
* `git log -p -2` -p显示每次提交的内容差异,-2显示最近两次提交,常用的还有`git log --graph`,`git log --pretty=oneline[short,full,fuller,format]`,`git log -Sfunctionname`,`git log --grep 关键字`其他的请参阅帮助
* `git commit --amend` amend 将用来修复上次提交,例如上次提交如果忘记了某些文件,可以使用此命令修复,git将会把amend的文件与之前的文件记录为一次提交
* `git reset HEAD 文件名.txt` 取消暂存
* `git checkout -- 文件名` 撤销对文件的修改, 比较危险,因为本地的修改可能会被从远端来的文件覆盖
* `git remote -v` 查看配置的远端仓库信息, -v显示git保存的简写和url
* `git remote add knstuct https://github.com/https://github.com/xuelingxiao/java-knowledge-structure` 添加远端仓库配置
* `git fetch knstuct` 获取仓库,即镜像同步到本地
* `git pull knstuct` 拉取远端分支到本地,并合并,fetch不会合并
* `git push -f remote-name branch-name` 推送到远端, -f将回滚版本(强制推送)
* `git remote show origin` 查看一个远端分支的更多信息
* `git remote rename oldname newname` 远端分支重命名
* `git remote rm branch-name` 移除远端分支 
* `git tag` 列出标签
* `git tag -l 'v1.8.5*'` 只列出v1.8.5系列的标签
* `git tag -a v1.1 -m 'v1.1版本的标签'` 创建一个附注标签(git标签分两类:轻量标签和附注标签,附注标签存储了git数据库中的一个完整对象,可以被检验,包含了打标签人的信息)
* `git tag v1.2 -lw` 打轻量标签
* `git push origin v1.1` 推送标签到远端,这样可以共享标签
* `git checkout -b brahchname tagname` 检出标签,实际是将标签版本检出到工作区 -b只是第一次checkout使用
* 别名设置, 参考示例如下
``` Shell
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status

$ git config --global alias.unstage 'reset HEAD --'
--上面命令运行后,下面两条语句等价
$ git unstage fileA
$ git reset HEAD -- fileA

--如果是外部命令, 可以在命令前加!
$ git config --global alias.visual '!gitk'
```
* `git merge branch master` 合并分支
* `git rebase master` 变基,掌握不住的话要少用

## Git-Flow
规划团队如何使用git, 即使用git的一套规范; 可以参考google的gitflow. 

## git hooks
可以在CI使用, 自动发布,与jenkins集成.

通过本次学习我们基本就可以应对平时的需要了.作为工程化的一部分,git就先了解这么多(后面如果有时间的话再整理下git的更多知识), 下一步将学习jenkins.