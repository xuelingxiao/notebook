# (三)Java工程化--Git起步

GIT学习参考：[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)

## 版本控制

版本控制记录了一个或若干文件的历史变化，便于今后查阅，恢复。

#### 三类版本控制系统

1. 本地版本控制系统 RCS : 本地存储文件变更系统,无法协作及对权限做统一管理
2. 集中化版本控制系统 CVCS : 变更存储于集中的一台服务器
3. 分布式版本控制系统 DVCS  : 分布式存储版本库镜像, 包含文件历史变更的所有信息

## Git的历史

git来自于linux团队， 是linux为了解决之前版本管理工具Bitkeeper收费的问题研发出来的。

设计目标

* 速度
* 简单
* 对非线性开发模式的强力支持(多个并行开发的分支)
* 完全分布式
* 适用超大规模项目

> linux是开源的, 所以当他们之前使用的版本工具开始收费的适合,他们决定自己研发一个版本控制工具,即Git. 

> 说起开源, 我们需要了解下常见的开源协议,以便我们做技术选型时考虑.例如一般的开源协议都要求使用开源框架的项目也要开源.

## Git与SVN(或者说其他版本控制系统)的区别

1. 直接记录快照,而非差异比较 
        
        了解此项差异的底层实现方式非常重要,有利于我们更准确的理解和学习Git.具体可以参考文章开始的网站资料.(有图有真相)

2.  近乎所有操作都在本地执行(得益于第一点的底层实现,即分布式存储)
3. Git使用sha1哈希算法算出的校验和保证完整性

        Git的索引是校验值而不是文件名,如果在传送过程中有信息丢失和损坏,Git就能发现.
4. Git一般只添加数据   (只要提交便不会丢失数据,可以执行可逆操作)

## 使用前的配置

* `git config --list` 显示所有配置
* `git config --global user.name 'user'` 设置用户名
* `git config --global user.email 'user@xxx.com'` 设置用户邮箱
* `ssh-keygen -t rsa -C 'user@xxx.com'` 生成ssh密钥
* 多用户配置方法: 在.ssh路径下(C:\Users\xueli\.ssh)创建文件config, 添加下面内容
<pre> 
 # Default github user(usergithub@mail.com)
Host github.com
  HostName github.com
  User git
  IdentityFile C:\Users\xueli\.ssh\id_rsa
  
 # Default mygitlib user(second@mail.com)
Host mygitlib.com
  HostName mygitlib.com
  User git
  IdentityFile C:\Users\xueli\.ssh\mygitlib
</pre>

上面是Git起步和背景知识, 下次将学习Git常用命令.