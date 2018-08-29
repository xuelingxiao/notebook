# (五)Java工程化--Jenkins

## Jenkins简介

Jenkins 是一种用Java语言实现的持续集成工具,Jenkins是一个平台, 在此基础上实现下面两个目的.

* CI 持续集成(Continous Integration)
* CD 持续交付(Continous Delivery)

## 安装

* 下载地址: https://jenkins.io/  文件名为jenkins.war
* 启动命令：java -jar jenkins.war --httpPort=8099
* 访问http://localhost:8099 第一次访问会有guide,按guide配置好用户/插件等
* 插件安装：建议安装推荐的插件， 如不安装插件有的配置项出不来；系统管理-->插件管理-->可选插件  可以查找和安装插件

## 配置 （进入“系统管理”菜单）

* 全局工具配置

        点击 系统管理-->全局工具配置  在此目录下配置JDK和MAVEN环境,以及git; (不安装git相关插件看不到配置项)
        JDK和Maven是配置home路径, git需要配置git.exe文件的全路径

* 创建任务

Jenkins的学习主要是要自己动手, 本文不再截图凑篇幅, 实践中遇到相应问题可以从管网查找资料,该下载插件的下插件,该在流程中作相应配置的做配置.
在我从上家公司离职之前的几个月, 公司的运维正在做CI方面的工作, 其间也是根据实际情况慢慢摸索, 一方面是要满足各种不同语言,项目,场景的CI, 另一方面也证实Jenkins的强大适应性,丰富的插件几乎能满足各种需求.
