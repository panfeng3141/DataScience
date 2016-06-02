##Git Notes

By panfeng3141  2015-5-10

---
###Git is what?

+ Git官方网站 http://git-scm.com

+ Git是分布式版本控制系统.

![]()

+ Working Directory & Repository

![](https://raw.githubusercontent.com/panfeng3141/pic/master/git.png)

###创建版本库

+ 创建一个空目录

`mkdir file`

`cd file`

`git init` #把当前目录变成git可托管的目录

+ 把文件添加到repository

`git add <file>` #把文件添加到仓库

`git commit -m"words about describing changes"` #把文件提交到仓库

###时光穿梭机

+ 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout file`

+ 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset --hard HEAD^`，就回到了场景1，第二步按场景1操作。

+ 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

`git reset --hard HEAD^` #版本回退至上个

`git reset --hard commit_id` #版本回退至指定commit_id

`git checkout --file` #撤销修改，返回到上一个状态

`git rm file` #从版本库删除文件（记得要提交）

`rm file` #从工作区删除文件

至此，终于拥有了真正的分布式版本库！

---
＋查看

`pwd` #显示当前目录位置

`git status` #查看当前库状态

`git diff <file>` #查看修改内容

`git log` #查看提交历史

`git log --pretty==oneline` #查看提交历史提纲

`git reflog` #查看历史命令

`cat file` #查看文件内容详情

###远程仓库

场景：已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。

+ 本地仓库与GitHub仓库设置

`ssh-keygen -t rsa -C "youremail@example.com"` ＃创建ssh key

`Add SSH Key` ＃登陆GitHub，打开“Account settings”，“SSH Keys”页面,点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

+ 添加远程仓库（先本地如何关联远程库）

`git remote add origin git@github.com:panfeng3141/learngit.git` ＃关联一个远程库

`git push -u origin master` ＃把本地库的所有内容推送到远程库上（由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。）

`git push origin master` 

+ 从远程库克隆（先远程库如何克隆到本地）

`git clone git@github.com:panfeng3141/gitskills.git`
＃克隆一个仓库（Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。）

###分支管理

理解什么git分支管理系统，情景栗子：

假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

解决方法：创建一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

+ 1. `HEAD`严格来说不是指向提交，而是指向master，master才是指向提交的，所以，`HEAD`指向的就是当前分支

![](https://raw.githubusercontent.com/panfeng3141/pic/master/master.png)

+ 2. 每次提交，master分支都会向前移动一步，master分支的线也越来越长：

![](https://raw.githubusercontent.com/panfeng3141/pic/master/master1.png)

+ 3. 创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把`HEAD`指向dev，就表示当前分支在dev上

![](https://raw.githubusercontent.com/panfeng3141/pic/master/fenzhi.png)

+ 4. 从现在开始，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针不变

![](https://github.com/panfeng3141/pic/raw/master/fenzhi1.png)

+ 5. 合并，直接把master指向dev的当前提交

![](https://raw.githubusercontent.com/panfeng3141/pic/master/fenzhi2.png)

+ 6. 删除分支，剩下了一条master分支，幡然醒悟，这些提交都是通过分支完成的

![](https://raw.githubusercontent.com/panfeng3141/pic/master/fenzhi3.png)

---

+ 创建与合并分支

`git checkout -b dev` ＃创建dev分支，然后切换到dev分支

`git branch dev` ＃创建一个叫dev分支

`git checkout dev` ＃切换到dev分支

`git branch` ＃查看当前分支列（当前分支前面会标一个*号）

 `git merge dev` ＃合并指定分支dev到当前分支
 
`git branch -d dev` ＃删除分支
 
+ 解决冲突

冲突是如何产生的？

如何解决冲突？

+ 分支管理策略

+ Bug分支

+ Feature分支

+ 多人协作

模拟场景栗子：


---

总结git在多人协作场景中的优势

###标签管理

发布一个版本时，我们通常先在版本库中打一个标签,唯一确定了打标签时刻的版本,方便存取。

+ 创建标签

创建的标签都只存储在本地，不会自动推送到远程

`git tag <name>`创建标签 ＃默认标签是打在最新提交的commit上的

`git tag`查看标签

 `git show <tagname>`查看标签信息
 
 场景：有时候，如果忘了打标签，比如，现在已经是周五了，但应该在周一打的标签没有打，怎么办？
 
 方法是找到历史提交的commit id，然后打上就可以了：
 
 `git tag <name> commit id`给制定commit id创建标签
 
+ 操作标签

推送本地标签到远程

`git push origin <tagname>`#推送一个本地标签

`git push origin --tags`#推送全部未推送过的本地标签

删除标签

`git tag -d <tagname>`删除本地一个本地标签

`git tag -d <tagname>`删除一个远程标签#先从本地删除

`git push origin :refs/tags/<tagname>`#再从远程删除

###使用GitHub

GitHub是什么？

+ 免费的远程仓库，存放个人的开源项目。

+ 是一个开源协作社区，通过GitHub，既可以让别人参与你的开源项目，也可以参与别人的开源项目。

step1 在GitHub上，可以任意Fork开源仓库；

step2 自己拥有Fork后的仓库的读写权限；

step3 可以推送pull request给官方仓库来贡献代码。

---

ps：一定要从自己的账号下clone仓库，这样你才能推送修改。如果从bootstrap的作者的仓库地址git@github.com:twbs/bootstrap.git克隆，因为没有权限，你将不能推送修改。

Bootstrap的官方仓库twbs/bootstrap、你在GitHub上克隆的仓库my/bootstrap，以及你自己克隆到本地电脑的仓库，他们的关系就像下图显示的那样：

![](https://raw.githubusercontent.com/panfeng3141/pic/master/fork.png)
 
###自定义Git

+ 搭建Git服务器

+ 忽略特殊文件

+ 配置别名

###相关学习资料

[`廖雪峰Git教程`](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

[`Git Cheat Sheet`](http://pan.baidu.com/s/1jGxjQL4#path=%252Fpub%252Fgit)

