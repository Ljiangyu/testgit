# 使用git的教程

## #相关的快捷操作键

* ![image-20231201085724002](C:\Users\江里的鱼\AppData\Roaming\Typora\typora-user-images\image-20231201085724002.png)
* ```github
  1.git bash 
  使用where ssh 可以来查看.ssh文件的路径和位置
  2.
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

