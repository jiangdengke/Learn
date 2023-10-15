# Git

## 为什么需要git？

因为需要一个工具来管理不同的版本，而git是一个最先进的的分布式版本工具（主要是开源免费）。补充：git是分布式版本控制，分布式版本控制怎么理解？与集中式版本控制对比来讲，集中式版本控制将项目放在一个服务器上，一旦这个服务器over，一切毁于一旦。因而分布式版本控制更受欢迎，而git恰恰是。

## 版本管理

### 概念

一句话:在开发的过程中用于管理对文件，目录或工程等内容的修改历史，方便查看历史记录，备份以便恢复到以前的版本的软件工程技术。

### 功能

1. 实现跨区域多人协同开发
2. 追踪和记载一个或多个文件的历史记录
3. 组织和保护你的源代码或文档
4. 统计工作量
5. 并行开发，提高开发效率
6. 跟踪记录整个软件的开发过程
7. 减轻开发人员负担，节省时间，同时降低人为错误

## Git基本配置

### 设置用户名和邮箱及配置SSH

##### 设置用户名

```java
git config --global user.name "jdk"
```

##### 设置邮箱

```java
git config --global user.email "000000000@qq.com"
```

##### 设置后的邮箱会在`c:\用户\Administrator\.gitconfig`下

##### 配置ssh

```Java
ssh-keygen -t rsa -C "这里换上你的邮箱"
```

然后将公钥放在需要配置的平台上即可

### 查看配置

##### 查看所有配置

```java
git config -l
```



##### 查看系统配置

```java
git config --system --list
```



##### 查看用户配置

```java
git config --global --list
```

## Git工作原理

##### 工作原理图解

![image-20231014195738344](C:\Users\jdk\AppData\Roaming\Typora\typora-user-images\image-20231014195738344.png)

1. Workspace:工作区，就是你平时存放项目代码的地方。
2. Stage(Index):暂存区，用于临时存放你的改动，事实上他只是一个文件，保存即将提交到文件列表信息。
3. Repository:仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本。
4. Remote Directory：远程仓库，托管代码的服务器（比如Github或Gitee）,可以简单的认为是你项目组中的一台电脑用于远程数据交换。

## Git工作流程

![image-20231014203038026](C:\Users\jdk\AppData\Roaming\Typora\typora-user-images\image-20231014203038026.png)

## Git常用命令

`git init`初始化本地仓库。

`git add . `将当前目录下未纳入版本控制的文件，纳入版本控制，也就是加入到暂存区。如果所有文件都未被版本控制，将会被版本控制。

`git commit -m "提交记录"`将暂存区的文件提交到本地仓库，-m 指定 提交提示信息。

`git remote add origin git@github.com:jiang/000.git`关联远程仓库

`git push -u origin master `将本地仓库的文件push到远程仓库（gitee或github等）。

## Git分支管理

##### 分支示意图

![image-20231015121220932](C:\Users\jdk\AppData\Roaming\Typora\typora-user-images\image-20231015121220932.png)

##### 注意

1. 分支可以有多个，根据业务需求
2. 如果各分支没有交集，始终平行发展，则不需要合并（merge）
3. 如果两个分支，需要合并，则执行merge操作

##### git分支命令

```# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```