---
title: Git & Github 相关
tags: Python
index_img: 
banner_img: https://git-scm.com/images/branching-illustration@2x.png
---

## Git & Github学习笔记

### 什么是Git？

分布式版本控制工具，代码版本控制。**目前世界上最先进的分布式版本控制系统。**

### 理论基础：

Git本地有三个工作区域：工作目录（Working Directory）、暂存区(Stage/Index)、资源库(Repository或Git Directory)。如果在加上远程的git仓库(Remote Directory)就可以分为四个工作区域。文件在这四个区域之间的转换关系如下：

![图片](https://s2.loli.net/2022/06/03/db4AVkoZl2wLQ8O.png)

从下到上依次是：

- 工作区：就是平时存放项目代码的地方。
- 暂存区：用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息。
- 仓库区（或本地仓库）：就是安全存放数据的位置，这里面有提交到所有版本的数据。其中HEAD指向最新放入仓库的版本。这个不算工作区，而是 Git 的版本库，里面有你提交到所有版本的数据。
- 远程仓库：托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换。

更清楚的图示：

![img](https://s2.loli.net/2022/06/03/kUfoABm6JFRWXjp.png)

##### 常用的工作步骤：

1. 在工作目录中添加、修改文件；
2. 将需要进行版本管理的文件放入暂存区域；
3. 将暂存区域的文件提交到git仓库。

git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交(committed)。



##### 分支：

**Git的分支**就是科幻电影里面的平行宇宙，如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，我们就需要处理一些问题了！

有两种产生冲突的原因：

- 合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。
- 有两套完全不同的修改。 Git无法替我们决定使用哪一个。必须 人为决定新代码内容。

解决的办法是我们可以修改冲突文件后重新提交！选择要保留他的代码还是你的代码！如下图：

:one:正常合并不冲突：

<img src="https://img-blog.csdnimg.cn/b4f384f593fd4f1bb8f8166cf7c3788a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA55Sf5ZG95piv5pyJ5YWJ55qE,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center" alt="img"  />

:two:合并产生冲突：

例如，我们首先在 master 分支的倒数第二行进行修改，并将其添加到暂存区，再提交到本地库。

![img](https://img-blog.csdnimg.cn/4821244a17a44193a41238f39b3bff2e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA55Sf5ZG95piv5pyJ5YWJ55qE,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

接着，我们去 hot-fix 分支的倒数第一行进行修改，并将其添加到暂存区，再提交到本地库

![img](https://img-blog.csdnimg.cn/2bcdd89a7c9d43a9bd6564359499b7c8.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA55Sf5ZG95piv5pyJ5YWJ55qE,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

之后我们在 master 分支上合并 hot-fix 分支，发现产生冲突

![img](https://img-blog.csdnimg.cn/4e603c5ffb3f4383a1082cade9b10a4d.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA55Sf5ZG95piv5pyJ5YWJ55qE,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

解决冲突的办法：编辑有冲突的文件，删除特殊符号（`<<<<<< HEAD` 当前分支的代码 `=======` 合并过来的代码 `>>>>>>>hot-fix`），决定要使用的内容。接着保存，再次添加到暂存区，并再次提交到本地库(注意：此时使用 git commit 命令时候不能带文件名)

![在这里插入图片描述](https://img-blog.csdnimg.cn/7ba8e844ff5f4062abe9a8c61763378a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA55Sf5ZG95piv5pyJ5YWJ55qE,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

master主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的dev分支上工作，工作完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。

##### 签名：

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看
到，以此确认本次提交是谁做的。 Git安装必须设置用户签名。这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系。

##### 初始化本地库：

在本地的需要管理的目录下，新建了一个.git隐藏文件夹，将该同级文件或者文件夹都添加入版本库（这个概念下面聊）。

##### 查看本地库状态：

查看当前工作区的git状态，如下图，我的小小计算器项目下使用`git status`：

![image-20220603145203556](https://s2.loli.net/2022/06/03/gnR95WOItJejXZS.png)

在文件发生更改的时候，会有四种状态：

- Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过`git add `状态变为Staged.
- Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用`git rm`移出版本库, 则成为Untracked文件
- Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用`git checkout `则丢弃修改过, 返回到unmodify状态, 这个`git checkout`即从库中取出文件, 覆盖当前修改 !
- Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行`git reset HEAD filename`取消暂存, 文件状态为Modified

##### 版本穿梭：

在git本地库中，软件会迭代很多版本，在不同版本之间切换便是版本穿梭。版本穿梭最重要的是知道想更换的版本的版本号，然后再使用上述命令。

------



### Git版本控制常用命令

|                 命令                  |        作用        |
| :-----------------------------------: | :----------------: |
|     git config --global user.name     |  设置全局用户签名  |
|    git config --global user.email     |        同上        |
|             **git init**              |  **初始化本地库**  |
|            **git status**             | **查看本地库状态** |
|          **git add 文件名**           |  **添加到暂存区**  |
| **git commit -m " 日志信息 " 文件名** |  **提交到本地库**  |
|            **git reflog**             |  **查看历史记录**  |
|      **git reset --hard 版本号**      |    **版本穿梭**    |

![img](https://s2.loli.net/2022/06/03/pwLfDJ41ehsTxkb.png)



### Git分支控制常用命令

|          命令          |              作用              |
| :--------------------: | :----------------------------: |
|   git branch 分支名    | 创建分支，但依然停留在当前分支 |
| git checkout -b 分支名 |  新建一个分支，并切换到该分支  |
|     git branch -v      |            查看分支            |
|  git checkout 分支名   |            切换分支            |
|  git branch -d 分支名  |            删除分支            |
|    git merge 分支名    |  把指定的分支合并到当前分支上  |

### Git远程仓库操作命令

|                  命令                  |                             作用                             |
| :------------------------------------: | :----------------------------------------------------------: |
|             git remote -v              |                   查看当前所有远程地址别名                   |
|      git remote add 别名 远程地址      |                            起别名                            |
|         **git push 别名 分支**         |              **推送本地分支上的内容到远程仓库**              |
|         **git clone 远程地址**         |                **将远程仓库的内容克隆到本地**                |
| **git pull 远程库地址别名 远程分支名** | **将远程仓库对于分支最新内容拉下来<br>后与当前本地分支直接合并** |

