# 使用git的教程

## #相关的快捷操作键

* ![image-20231201085724002](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201085724002.png)
* ```github
  1.git bash 
  使用where ssh 可以来查看.ssh文件的路径和位置
  2.
  ```
* ```github
  一、新建代码库
  
  # 在当前目录新建一个Git代码库
  $ git init
  
  # 新建一个目录，将其初始化为Git代码库
  $ git init [project-name] # 下载一个项目和它的整个代码历史
  $ git clone [url]
  
  二、配置
  # 显示当前的Git配置
  $ git config --list
  
  # 编辑Git配置文件
  $ git config -e [--global] # 设置提交代码时的用户信息
  $ git config [--global] user.name "[name]"
  $ git config [--global] user.email "[email address]"
  
  三、增加/删除文件
  # 添加指定文件到暂存区
  $ git add [file1] [file2] ... # 添加指定目录到暂存区，包括子目录
  $ git add [dir] # 添加当前目录的所有文件到暂存区
  $ git add . # 添加每个变化前，都会要求确认 # 对于同一个文件的多处变化，可以实现分次提交
  $ git add -p
  
  # 删除工作区文件，并且将这次删除放入暂存区
  $ git rm [file1] [file2] ... # 停止追踪指定文件，但该文件会保留在工作区
  $ git rm --cached [file] # 改名文件，并且将这个改名放入暂存区
  $ git mv [file-original] [file-renamed]
  
  四、代码提交
  # 提交暂存区到仓库区
  $ git commit -m [message] # 提交暂存区的指定文件到仓库区
  $ git commit [file1] [file2] ... -m [message] # 提交工作区自上次commit之后的变化，直接到仓库区
  $ git commit -a
  
  # 提交时显示所有diff信息
  $ git commit -v
  
  # 使用一次新的commit，替代上一次提交 # 如果代码没有任何新变化，则用来改写上一次commit的提交信息
  $ git commit --amend -m [message] # 重做上一次commit，并包括指定文件的新变化
  $ git commit --amend [file1] [file2] ...
  
  五、分支
  # 列出所有本地分支
  $ git branch
  
  # 列出所有远程分支
  $ git branch -r
  
  # 列出所有本地分支和远程分支
  $ git branch -a
  
  # 新建一个分支，但依然停留在当前分支
  $ git branch [branch-name] # 新建一个分支，并切换到该分支
  $ git checkout -b [branch] # 新建一个分支，指向指定commit
  $ git branch [branch] [commit] # 新建一个分支，与指定的远程分支建立追踪关系
  $ git branch --track [branch] [remote-branch] # 切换到指定分支，并更新工作区
  $ git checkout [branch-name] # 切换到上一个分支
  $ git checkout - # 建立追踪关系，在现有分支与指定的远程分支之间
  $ git branch --set-upstream [branch] [remote-branch] # 合并指定分支到当前分支
  $ git merge [branch] # 选择一个commit，合并进当前分支
  $ git cherry-pick [commit] # 删除分支
  $ git branch -d [branch-name] # 删除远程分支
  $ git push origin --delete [branch-name]
  $ git branch -dr [remote/branch]
  
  六、标签
  # 列出所有tag
  $ git tag
  
  # 新建一个tag在当前commit
  $ git tag [tag] # 新建一个tag在指定commit
  $ git tag [tag] [commit] # 删除本地tag
  $ git tag -d [tag] # 删除远程tag
  $ git push origin :refs/tags/[tagName] # 查看tag信息
  $ git show [tag] # 提交指定tag
  $ git push [remote] [tag] # 提交所有tag
  $ git push [remote] --tags
  
  # 新建一个分支，指向某个tag
  $ git checkout -b [branch] [tag]
  
  七、查看信息
  # 显示有变更的文件
  $ git status
  
  # 显示当前分支的版本历史
  $ git log
  
  # 显示commit历史，以及每次commit发生变更的文件
  $ git log --stat
  
  # 搜索提交历史，根据关键词
  $ git log -S [keyword] # 显示某个commit之后的所有变动，每个commit占据一行
  $ git log [tag] HEAD --pretty=format:%s
  
  # 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
  $ git log [tag] HEAD --grep feature
  
  # 显示某个文件的版本历史，包括文件改名
  $ git log --follow [file]
  $ git whatchanged [file] # 显示指定文件相关的每一次diff
  $ git log -p [file] # 显示过去5次提交
  $ git log -5 --pretty --oneline
  
  # 显示所有提交过的用户，按提交次数排序
  $ git shortlog -sn
  
  # 显示指定文件是什么人在什么时间修改过
  $ git blame [file] # 显示暂存区和工作区的差异
  $ git diff
  
  # 显示暂存区和上一个commit的差异
  $ git diff --cached [file] # 显示工作区与当前分支最新commit之间的差异
  $ git diff HEAD
  
  # 显示两次提交之间的差异
  $ git diff [first-branch]...[second-branch] # 显示今天你写了多少行代码
  $ git diff --shortstat "@{0 day ago}" # 显示某次提交的元数据和内容变化
  $ git show [commit] # 显示某次提交发生变化的文件
  $ git show --name-only [commit] # 显示某次提交时，某个文件的内容
  $ git show [commit]:[filename] # 显示当前分支的最近几次提交
  $ git reflog
  
  八、远程同步
  # 下载远程仓库的所有变动
  $ git fetch [remote] # 显示所有远程仓库
  $ git remote -v
  
  # 显示某个远程仓库的信息
  $ git remote show [remote] # 增加一个新的远程仓库，并命名
  $ git remote add [shortname] [url] # 取回远程仓库的变化，并与本地分支合并
  $ git pull [remote] [branch] # 上传本地指定分支到远程仓库
  $ git push [remote] [branch] # 强行推送当前分支到远程仓库，即使有冲突
  $ git push [remote] --force
  
  # 推送所有分支到远程仓库
  $ git push [remote] --all
  
  九、撤销
  # 恢复暂存区的指定文件到工作区
  $ git checkout [file] # 恢复某个commit的指定文件到暂存区和工作区
  $ git checkout [commit] [file] # 恢复暂存区的所有文件到工作区
  $ git checkout . # 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
  $ git reset [file] # 重置暂存区与工作区，与上一次commit保持一致
  $ git reset --hard
  
  # 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
  $ git reset [commit] # 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
  $ git reset --hard [commit] # 重置当前HEAD为指定commit，但保持暂存区和工作区不变
  $ git reset --keep [commit] # 新建一个commit，用来撤销指定commit # 后者的所有变化都将被前者抵消，并且应用到当前分支
  $ git revert [commit] # 暂时将未提交的变化移除，稍后再移入
  $ git stash
  $ git stash pop
  ```
* 

## 一、账户的链接

​	1.git config --global user.name "Ljiangyu"
​	2.git config --global user.email "li2021_0912@qq.com"

## 二、相关快捷键的操作

### 	1 创建版本库

​		cd D:  //移动到D盘
​		cd www
​		//移动到www
​		mkdir testgit
​		//创建文件testgit
​		cd testgit 
​		//移动到testgit
​		pwd
​		//显示当前路径
​		（1）使用git init 将这个目录变成git 可以管理的仓库

#使用git的教程
一、账户的链接
	1.git config --global user.name "Ljiangyu"
	2.git config --global user.email "li2021_0912@qq.com"
二、相关快捷键的操作

### 	1 创建版本库

​		cd D:  //移动到D盘
​		cd www
​		//移动到www
​		mkdir testgit
​		//创建文件testgit
​		cd testgit 
​		//移动到testgit
​		pwd
​		//显示当前路径
​		（1）使用git init 将这个目录变成git 可以管理的仓库

#使用git的教程
一、账户的链接
	1.git config --global user.name "Ljiangyu"
	2.git config --global user.email "li2021_0912@qq.com"

### 二、相关快捷键的操作

#### 	1 创建版本库

​		cd D:  //移动到D盘
​		cd www
​		//移动到www
​		mkdir testgit
​		//创建文件testgit
​		cd testgit 
​		//移动到testgit
​		pwd
​		//显示当前路径

*  使用git init 将这个目录变成git 可以管理的仓库
* 

![](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201065857922.png)



* 在testgit目录下，创建一个readme文件
* 使用**git add readme.txt**添加到暂存区中
* 使用命令**git commit** 进行注释 将文件提交到仓库
* 现在我们已经提交了一个readmetxt文件使用git status查看是否文件提交成功
* 使用git diff 文件名 可以来查看文件更改的内容
* ![image-20231201071248582](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201071248582.png)



#### 2 版本回退

* 使用git log可以查看历史记录，需要注意的是最多只能看三次的记录
* 进行版本回退操作
  * 有两种方式
  * git reset --hard HEAD^,以此类推加^
  * 对于大规模的版本回退git reset --hard HEAD~100,直接回退100版本
* 查看内容命令 cat readme.txt
* ![image-20231201072317400](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201072317400.png)
* **如果在想回退到最新的版本**
  * 1.git reset  --hard +版本号
  * 2.**建立不几道版本号的情况下**使用git reflog 可以获得版本号。
  * ![image-20231201082959191](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201082959191.png)

## 三、工作区与暂存区的区别

### 1.相关介绍

* **工作区：**就是你在电脑上看到的目录，比如目录下testgit里的文件(.git隐藏目录版本库除外)。或者以后需要再新建的目录文件等等都属于工作区范畴。
  **版本库(Repository)：**工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。

  我们前面说过使用Git提交文件到版本库有两步：

  第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。

  第二步：使用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支上。

* ***这个也确实没有什么可以细说的，主要就是概念的理解***

## 四、git撤销修改和删除文件操作

### 一、撤销修改

* 第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit掉。

  第二：我可以按以前的方法直接恢复到上一个版本。使用 git reset --hard HEAD^

* 如果不想使用以上两种方法

* 当然需要经常使用git status，再次之前已经加入了555

* 使用指令git checkout -- file可以丢弃工作区的修改

* ![image-20231201084252459](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201084252459.png)

* 需要注意的有两点

* **1.readme.txt自动修改后**，还没有放到暂存区，使用 撤销修改就回到和版本库一模一样的状态。
  **2.另外一种是readme.txt已经放入暂存区了，**接着又作了修改，撤销修改就回到添加暂存区后的状态。
  对于第二种情况，我想我们继续做demo来看下，假如现在我对readme.txt添加一行 内容为6666666666666，我git add 增加到暂存区后，接着添加内容7777777，我想通过撤销命令让其回到暂存区后的状态。如下所示：

* **注意：命令git checkout -- readme.txt 中的 -- 很重要，如果没有 -- 的话，那么命令变成创建分支了。**

### 二、删除文件

* 假如我现在版本库testgit目录添加一个文件b.txt,然后提交。如下：
* ![img](https://pic2.zhimg.com/v2-a3160769ebe554f2fa08fb2c1f229569_r.jpg)
* 一般情况下，可以直接在文件目录中把文件删了，或者使用如上rm命令：rm b.txt ，如果我想彻底从版本库中删掉了此文件的话，可以再执行commit命令 提交掉，现在目录是这样的，
* 只要没有提交之前可以使用git checkout -- b.txt

## 五、远程仓库

### 1.建立远程链接

* ```github
  使用到的指令
  git remote add origin https://github.com/Ljiangyu/testgit.git
  建立链接
  git push -u origin master 
  将本地文件推送到远端
  ```

* 目前，在GitHub上的这个testgit仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。

  ```text
  现在，我们根据GitHub的提示，在本地的testgit仓库下运行命令：
  ```

  git remote add origin [https://github.com/tugenhua0707/testgit.git](https://link.zhihu.com/?target=https%3A//github.com/tugenhua0707/testgit.git)

  所有的如下：

  ![img](https://pic3.zhimg.com/80/v2-c862a425b87eee36326e49e67397d292_720w.webp)

  

  把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。

  由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。推送成功后，可以立刻在github页面中看到远程库的内容已经和本地一模一样了，上面的要输入github的用户名和密码如下所示：

  ![img](https://pic1.zhimg.com/80/v2-9ff3182d6256c26f94dff72e3d06ebbc_720w.webp)

  

  从现在起，只要本地作了提交，就可以通过如下命令：

  git push origin master

  把本地master分支的最新修改推送到github上了，现在你就拥有了真正的分布式版本库了。

  1. 如何从远程库克隆？

  上面我们了解了先有本地库，后有远程库时候，如何关联远程库。

  现在我们想，假如远程库有新的内容了，我想克隆到本地来 如何克隆呢？

  首先，登录github，创建一个新的仓库，名字叫testgit2.如下：

  ![img](https://pic4.zhimg.com/80/v2-f0fc0d64cad20ce60ac8c65a2241d71b_720w.webp)

  

  如下，我们看到：

  ![img](https://pic4.zhimg.com/80/v2-4d4ededd84604ca6c2f36cbdeefb8633_720w.webp)

  

  现在，远程库已经准备好了，下一步是使用命令git clone克隆一个本地库了。如下所示：

  ![img](https://pic3.zhimg.com/80/v2-e0d86da4a80c40350b1a9e7db25bb776_720w.webp)

  

  接着在我本地目录下 生成testgit2目录了，如下所示：

  ![img](https://pic2.zhimg.com/80/v2-6a2e48966004fa5ac328ad04b40fe721_720w.webp)

  

* ![image-20231201215611404](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201215611404.png)
* **自己演示的过程**
* ![image-20231201215626213](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201215626213.png)

* 

## 六、创建与合并分支

* 在 版本回填退里，你已经知道，每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

  首先，我们来创建dev分支，然后切换到dev分支上。如下操作：

* ![image-20231201222700473](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201222700473.png)

* ![image-20231201222735969](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201222735969.png)

* git branch获取当前的分支

* git checkout 命令加上 –b参数表示创建并切换，相当于如下2条命令

  git branch dev

  git checkout dev

  git branch查看分支，会列出所有的分支，当前分支前面会添加一个星号。然后我们在dev分支上继续做demo，比如我们现在在readme.txt再增加一行

  7777777777777

  首先我们先来查看下readme.txt内容，接着添加内容77777777，如下：现在dev分支工作已完成，现在我们切换到主分支master上，继续查看readme.txt内容如下：

* 演示示例

* ![image-20231201223253692](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201223253692.png)

* 到了这一步考虑内容合并操作

* 将dev分支上的内容合并到master上，使用git merge dev

* ![image-20231201223549367](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201223549367.png)

* git merge命令用于合并指定分支到当前分支上，合并后，再查看readme.txt内容，可以看到，和dev分支最新提交的是完全一样的。

  注意到上面的Fast-forward信息，Git告诉我们，这次合并是“快进模式”，也就是直接把master指向dev的当前提交，所以合并速度非常快。

  合并完成后，我们可以接着删除dev分支了，操作如下：

* 在这里想到了git的提交结构一条直线加上上下浮动的浮标

* ![image-20231201223929725](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201223929725.png)

* ```github
  总结创建与合并分支命令如下：
  
  查看分支：git branch
  
  创建分支：git branch name
  
  切换分支：git checkout name
  
  创建+切换分支：git checkout –b name
  
  合并某分支到当前分支：git merge name
  
  删除分支：git branch –d name
  ```

* 如何解决冲突？
  下面我们还是一步一步来，先新建一个新分支，比如名字叫fenzhi1，在readme.txt添加一行内容8888888，然后提交，如下所示：

  ![img](https://pic2.zhimg.com/80/v2-03610532a3b8b1c85275807865a4a7f9_720w.webp)

  同样，我们现在切换到master分支上来，也在最后一行添加内容，内容为99999999，如下所示：

  ![img](https://pic4.zhimg.com/80/v2-13321a0264baf62e552f99e6d9e86baf_720w.webp)

  

  现在我们需要在master分支上来合并fenzhi1，如下操作：

  ![img](https://pic4.zhimg.com/80/v2-06ebf4d925acdd3b0a63252d1534a11f_720w.webp)

  

  Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，其中<<<HEAD是指主分支修改的内容，>>>>>fenzhi1 是指fenzhi1上修改的内容，我们可以修改下如下后保存：

  ![img](https://pic1.zhimg.com/80/v2-5f225d5ae073928011bc1caa1aee6bd0_720w.webp)

  

  如果我想查看分支合并的情况的话，需要使用命令 git log.命令行演示如下：

  ![img](https://pic2.zhimg.com/80/v2-076cd2c7aa77fa3af48c141c2110de59_720w.webp)

  

  3.分支管理策略。

  通常合并分支时，git一般使用”Fast forward”模式，在这种模式下，删除分支后，会丢掉分支信息，现在我们来使用带参数 –no-ff来禁用”Fast forward”模式。首先我们来做demo演示下：

  ```text
  创建一个dev分支。
  修改readme.txt内容。
  添加到暂存区。
  切换回主分支(master)。
  合并dev分支，使用命令 git merge –no-ff -m “注释” dev
  查看历史记录
  截图如下：
  ```

  ![img](https://pic2.zhimg.com/80/v2-836def06f556a4bcf11ec9b71f73cf7d_720w.webp)

  

  分支策略：首先master主分支应该是非常稳定的，也就是用来发布新版本，一般情况下不允许在上面干活，干活一般情况下在新建的dev分支上干活，干完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。



## 七、bug分支

* 在开发中，会经常碰到bug问题，那么有了bug就需要修复，在Git中，分支是很强大的，每个bug都可以通过一个临时分支来修复，修复完成后，合并分支，然后将临时的分支删除掉。

* 比如我在开发中接到一个404 bug时候，我们可以创建一个404分支来修复它，但是，当前的dev分支上的工作还没有提交。比如如下：

![img](https://pic4.zhimg.com/80/v2-41b33769be53309db6c4270f25b90207_720w.webp)



* 并不是我不想提交，而是工作进行到一半时候，我们还无法提交，比如我这个分支bug要2天完成，但是我issue-404 bug需要5个小时内完成。怎么办呢？还好，Git还提供了一个stash功能，可以把当前工作现场 ”隐藏起来”，等以后恢复现场后继续工作。如下：

![img](https://pic1.zhimg.com/80/v2-21ff573d2e26de7e9f8da358eb972440_720w.webp)



* 所以现在我可以通过创建issue-404分支来修复bug了。

* 首先我们要确定在那个分支上修复bug，比如我现在是在主分支master上来修复的，现在我要在master分支上创建一个临时分支，演示如下：

![img](https://pic2.zhimg.com/80/v2-0f85ba33d14cf7a046c4ec94963e8f41_720w.webp)



* 修复完成后，切换到master分支上，并完成合并，最后删除issue-404分支。演示如下：

![img](https://pic3.zhimg.com/80/v2-c1ed199b5fa6d005cdc85e58be05a68e_720w.webp)

现在，我们回到dev分支上干活了。

![img](https://pic1.zhimg.com/80/v2-9c81c02d6aa4097739d907aad0846d60_720w.webp)



工作区是干净的，那么我们工作现场去哪里呢？我们可以使用命令 git stash list来查看下。如下：

![img](https://pic4.zhimg.com/80/v2-52b40415cdaecdbf18d9d5e3e9fac97b_720w.webp)



* 工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，可以使用如下2个方法：

* 1.git stash apply恢复，恢复后，stash内容并不删除，你需要使用命令git stash drop来删除。
  2.另一种方式是使用git stash pop,恢复的同时把stash内容也删除了。
  演示如下

![img](https://pic1.zhimg.com/80/v2-74d4c3a2588e5960094e96d11ffbae44_720w.webp)



## **八：多人协作**。

当你从远程库克隆时候，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且远程库的默认名称是origin。

要查看远程库的信息 使用 git remote
要查看远程库的详细信息 使用 git remote –v
如下演示：

![img](https://pic1.zhimg.com/80/v2-36fdbe428a09ee0f95c48487172acb5c_720w.webp)



一：推送分支：

推送分支就是把该分支上所有本地提交到远程库中，推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：

使用命令 git push origin master

```text
比如我现在的github上的readme.txt代码如下：
```

![img](https://pic1.zhimg.com/80/v2-64a5f2e5d632a91078d40fae03df09a4_720w.webp)



本地的readme.txt代码如下：

![img](https://pic3.zhimg.com/80/v2-771864800269580136a176b5228f9586_720w.webp)



现在我想把本地更新的readme.txt代码推送到远程库中，使用命令如下：

![img](https://pic4.zhimg.com/80/v2-271eabd81fb65641a3a4a87ae7454cc3_720w.webp)



我们可以看到如上，推送成功，我们可以继续来截图github上的readme.txt内容 如下：

![img](https://pic1.zhimg.com/80/v2-771f47ef089ddf78beb3c3111b34b84c_720w.webp)



可以看到 推送成功了，如果我们现在要推送到其他分支，比如dev分支上，我们还是那个命令 git push origin dev

那么一般情况下，那些分支要推送呢？

master分支是主分支，因此要时刻与远程同步。
一些修复bug分支不需要推送到远程去，可以先合并到主分支上，然后把主分支master推送到远程去。
二：抓取分支：

多人协作时，大家都会往master分支上推送各自的修改。现在我们可以模拟另外一个同事，可以在另一台电脑上（注意要把SSH key添加到github上）或者同一台电脑上另外一个目录克隆，新建一个目录名字叫testgit2

但是我首先要把dev分支也要推送到远程去，如下

![img](https://pic1.zhimg.com/80/v2-4adfaa848b49797969c4815e662fb8a4_720w.webp)



接着进入testgit2目录，进行克隆远程的库到本地来，如下：

![img](https://pic2.zhimg.com/80/v2-ec7665a72d0371f02ae54515c31d836d_720w.webp)



现在目录下生成有如下所示：

![img](https://pic1.zhimg.com/80/v2-9427ca3d7bcfc9bc8726b3f3a58a0c34_720w.webp)

现在我们的小伙伴要在dev分支上做开发，就必须把远程的origin的dev分支到本地来，于是可以使用命令创建本地dev分支：git checkout –b dev origin/dev

现在小伙伴们就可以在dev分支上做开发了，开发完成后把dev分支推送到远程库时。

如下：

![img](https://pic4.zhimg.com/80/v2-ef1e424ff4b786ad2c807e85d1b02097_720w.webp)



小伙伴们已经向origin/dev分支上推送了提交，而我在我的目录文件下也对同样的文件同个地方作了修改，也试图推送到远程库时，如下：

![img](https://pic3.zhimg.com/80/v2-20930f0e0f2b40d67fab7e901f39f4f6_720w.webp)



由上面可知：推送失败，因为我的小伙伴最新提交的和我试图推送的有冲突，解决的办法也很简单，上面已经提示我们，先用git pull把最新的提交从origin/dev抓下来，然后在本地合并，解决冲突，再推送。

![img](https://pic2.zhimg.com/80/v2-473eefb758a8d6f988b10726df10e8b9_720w.webp)



git pull也失败了，原因是没有指定本地dev分支与远程origin/dev分支的链接，根据提示，设置dev和origin/dev的链接：如下：

![img](https://pic4.zhimg.com/80/v2-59c145e428839f7cdbb330b2f6715a63_720w.webp)



这回git pull成功，但是合并有冲突，需要手动解决，解决的方法和分支管理中的 解决冲突完全一样。解决后，提交，再push：
我们可以先来看看readme.txt内容了。

![img](https://pic2.zhimg.com/80/v2-a87639c3d8c403ecc7a57129a95f62bd_720w.webp)



现在手动已经解决完了，我接在需要再提交，再push到远程库里面去。如下所示：

![img](https://pic2.zhimg.com/80/v2-843923acc1cebca0501f6ab7eddb31bd_720w.webp)



因此：多人协作工作模式一般是这样的：

首先，可以试图用git push origin branch-name推送自己的修改.
如果推送失败，则因为远程分支比你的本地更新早，需要先用git pull试图合并。
如果合并有冲突，则需要解决冲突，并在本地提交。再用git push origin branch-name推送。
