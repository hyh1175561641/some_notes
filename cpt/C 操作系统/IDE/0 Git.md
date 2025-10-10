https://docs.github.com/en/desktop/overview/github-desktop-keyboard-shortcuts






https://git-scm.com/

https://git-scm.com/downloads/win








https://github.com/



https://github.com/apps/desktop
https://desktop.github.com/download/




https://docs.github.com/
https://docs.github.com/en/get-started







```markdown




### 分支

# 列出所有本地分支
$ git branch

git branch -r 列出所有远程分支
git branch -a 列出所有本地分支和远程分支
git branch [branch-name] 新建一个分支,但依然停留在当前分支
git checkout -b [branch] 新建一个分支,并切换到该分支
git branch [branch] [commit] 新建一个分支,指向指定commit
git branch --track [branch] [remote-branch] 新建一个分支,与指定的远程分支建立追踪关系
git checkout [branch-name] 切换到指定分支,并更新工作区
git checkout - 切换到上一个分支
git branch --set-upstream [branch] [remote-branch]建立追踪关系,在现有分支与指定的远程分支之间
git merge [branch] 合并指定分支到当前分支
git cherry-pick [commit] 选择一个commit,合并进当前分支
git branch -d [branch-name] 删除分支

删除远程分支
git push origin --delete [branch-name]
git branch -dr [remote/branch]


### 标签

git tag 列出所有tag
git tag [tag] 新建一个tag在当前commit
git tag [tag] [commit] 新建一个tag在指定commit
git tag -d [tag] 删除本地tag
git push origin :refs/tags/[tagName] 删除远程tag
git show [tag] 查看tag信息
git push [remote] [tag] 提交指定tag
git push [remote] --tags 提交所有tag
git checkout -b [branch] [tag] 新建一个分支,指向某个tag



### 查看信息
git status 显示有变更的文件
git log 显示当前分支的版本历史
git log --stat 显示commit历史,以及每次commit发生变更的文件
git log -S [keyword] 搜索提交历史,根据关键词
git log [tag] HEAD --pretty=format:%s 显示某个commit之后的所有变动,每个commit占据一行
git log [tag] HEAD --grep feature 显示某个commit之后的所有变动,其"提交说明"必须符合搜索条件

显示某个文件的版本历史,包括文件改名
git log --follow [file]
git whatchanged [file]

git log -p [file] 显示指定文件相关的每一次diff
git log -5 --pretty --oneline 显示过去5次提交
git shortlog -sn 显示所有提交过的用户,按提交次数排序
git blame [file] 显示指定文件是什么人在什么时间修改过
git diff 显示暂存区和工作区的差异
git diff --cached [file] 显示暂存区和上一个commit的差异
git diff HEAD 显示工作区与当前分支最新commit之间的差异
git diff [first-branch]...[second-branch] 显示两次提交之间的差异
git diff --shortstat "@{0 day ago}" 显示今天你写了多少行代码
git show [commit] 显示某次提交的元数据和内容变化
git show --name-only [commit] 显示某次提交发生变化的文件
git show [commit]:[filename] 显示某次提交时,某个文件的内容
git reflog 显示当前分支的最近几次提交



### 远程同步
git fetch [remote] 下载远程仓库的所有变动
git remote -v 显示所有远程仓库
git remote show [remote] 显示某个远程仓库的信息
git remote add [shortname] [url] 增加一个新的远程仓库,并命名

git pull [remote] [branch] 取回远程仓库的变化,并与本地分支合并
git push [remote] [branch] 上传本地指定分支到远程仓库
git push [remote] --force 强行推送当前分支到远程仓库,即使有冲突
git push [remote] --all 推送所有分支到远程仓库

### 撤销
git checkout [file] 恢复暂存区的指定文件到工作区
git checkout [commit] [file] 恢复某个commit的指定文件到暂存区和工作区
git checkout . 恢复暂存区的所有文件到工作区
git reset [file] 重置暂存区的指定文件,与上一次commit保持一致,但工作区不变
git reset --hard 重置暂存区与工作区,与上一次commit保持一致
git reset [commit] 重置当前分支的指针为指定commit,同时重置暂存区,但工作区不变
git reset --hard [commit] 重置当前分支的HEAD为指定commit,同时重置暂存区和工作区,与指定commit一致
git reset --keep [commit] 重置当前HEAD为指定commit,但保持暂存区和工作区不变

新建一个commit,用来撤销指定commit
后者的所有变化都将被前者抵消,并且应用到当前分支
git revert [commit]

暂时将未提交的变化移除,稍后再移入
git stash
git stash pop








```






# 正式开始的地方

https://git-scm.com/
https://git-scm.com/book/zh/v2
https://git-scm.com/docs/git-log

https://github.com/
https://docs.github.com/
https://support.github.com/


https://gitee.com/all-about-git
https://www.liaoxuefeng.com/wiki/896043488029600
https://www.runoob.com/git/git-tutorial.html
https://www.jianshu.com/p/e57a4a2cf077

https://gitee.com/ 码云
https://gitcode.com/ CSDN的git仓库



# Git

Git是一个开源的分布式版本控制系统
Git是Linus Torvalds为了帮助管理Linux内核开发而开发的一个开放源码的版本控制软件
分布式版本控制工具，SVN是集中式版本控制工具



安装与配置
```sh
# 源码安装
$ tar -zxf git-1.7.2.2.tar.gz
$ cd git-1.7.2.2
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```

命令行
```
$ git
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:这些是各种场合常见的Git命令

start a working area (see also: git help tutorial)开始一个工作区（参见：git help tutorial）
   clone      Clone a repository into a new directory克隆一个仓库到一个新目录
   init       Create an empty Git repository or reinitialize an existing one创建一个空的Git仓库或重新初始化一个已存在的仓库

work on the current change (see also: git help everyday)在当前变更上工作（参见：git help everyday）
   add        Add file contents to the index添加文件内容至索引
   mv         Move or rename a file, a directory, or a symlink移动或重命名一个文件、目录或符号链接
   reset      Reset current HEAD to the specified state重置当前HEAD到指定状态
   rm         Remove files from the working tree and from the index从工作区和索引中删除文件

examine the history and state (see also: git help revisions)查看历史和状态（参见：git help revisions）
   bisect     Use binary search to find the commit that introduced a bug通过二分查找定位引入bug的提交
   grep       Print lines matching a pattern输出和模式匹配的行
   log        Show commit logs显示提交日志
   show       Show various types of objects显示各种类型的对象
   status     Show the working tree status显示工作区状态

grow, mark and tweak your common history扩展、标记和调校您的历史记录
   branch     List, create, or delete branches列出、创建或删除分支
   checkout   Switch branches or restore working tree files切换分支或恢复工作区文件
   commit     Record changes to the repository记录变更到仓库
   diff       Show changes between commits, commit and working tree, etc显示提交之间、提交和工作区之间等的差异
   merge      Join two or more development histories together合并两个或更多开发历史
   rebase     Reapply commits on top of another base tip本地提交转移至更新后的上游分支中
   tag        Create, list, delete or verify a tag object signed with GPG创建、列出、删除或校验一个GPG签名的标签对象

collaborate (see also: git help workflows)协同（参见：git help workflows）
   fetch      Download objects and refs from another repository从另外一个仓库下载对象和引用
   pull       Fetch from and integrate with another repository or a local branch获取并整合另外的仓库或一个本地分支
   push       Update remote refs along with associated objects更新远程引用和相关的对象

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.

```



# 基础
一般工作流程如下
克隆Git资源作为工作目录
在克隆的资源上添加或修改文件
如果其他人修改了,你可以更新资源
在提交前查看修改
在修改完成后,如果发现错误,可以撤回提交并再次修改并提交

工作区、暂存区和版本库
工作区：电脑里面能看到的目录
暂存区：英文叫stage,或index。一般存放在.git目录下的index文件,有时称暂存区为索引index
版本库：工作区有一个隐藏目录,这个不算工作区,而是版本库

本地操作: 先创建好仓库
```bash
# 到达一个目录下面,将它初始化,执行完命令之后会生成一个.git目录
git init 
git init  在当前目录下生成.git目录
git init [newrepo] 新建一个目录,将其初始化为Git代码库


# git add增加文件
git add .  添加当前文件的所有文件
git add *.c  将目录下的*.c文件提交到暂存区中
git add [dir] 添加指定目录到暂存区,包括子目录
git add [file1] [file2] ...  添加指定文件到暂存区

?# 添加每个变化前,都会要求确认
?# 对于同一个文件的多处变化,可以实现分次提交
?git add -p



# git status
git status  查看状态信息
git status -s  查看项目的当前状态的简短输出
状态：
A  添加了文件
AM  添加到缓存之后又有改动

# git diff
git diff  尚未缓存的改动
git diff --cached  查看已缓存的改动
git diff HEAD  查看已缓存或未缓存的所有改动
git diff --stat  显示摘要而非整个diff

# git reset
git reset HEAD  取消已缓存的内容

# git rm
git rm file  删除文件
git rm [file1] [file2] ... 删除工作区文件,并且将这次删除放入暂存区
git rm -f file  强制删除已经缓存的文件
git rm --cached file  把文件藏暂存区移除,但是保留文件
git rm --cached [file] 停止追踪指定文件,但该文件会保留在工作区
git rm -r *  可以递归删除子文件和子目录

# git mv
get mv
git mv cc.c c.c  移动文件或重命名
git mv [file-original] [file-renamed] 改名文件,并且将这个改名放入暂存区


# git commit差不多之后,提交到版本库
git commit -m "写上备注"  将暂存区的内容添加到版本库中,提交暂存区到仓库区
git commit -a  直接将修改提交到版本库,提交工作区自上次commit之后的变化,直接到仓库区
git commit -am "写上备注"  上面两个的组合
git commit -v提交时显示所有diff信息
git commit [file1] [file2] ... -m [message]提交暂存区的指定文件到仓库区

使用一次新的commit,替代上一次提交
如果代码没有任何新变化,则用来改写上一次commit的提交信息
git commit --amend -m [message]

重做上一次commit,并包括指定文件的新变化
git commit --amend [file1] [file2] ...


# git log
git log  查看提交历史
git log --oneline  查看历史的简洁版本
git log --graph  查看历史的分支、合并记录
git log --reverse  逆向查看历史

# git reflog
git reflog 查看完整的提交历史

# git config配置信息
git config --list显示当前的Git配置
git config -e [--global]编辑Git配置文件
git config [--global] user.name "[name]" 设置提交代码时的用户信息
git config [--global] user.email "[email address]"




# 其他
# 生成一个可供发布的压缩包
git archive


```




# 分支管理

创建分支,切换分支,合并分支,当切换分支的时候,Git会用该分支的最后提交的快照替换你的工作目录内容,所以多个分支不需要多个目录

```bash
# git branch https://www.runoob.com/git/git-branch.html

# git checkout可以把代码一键还原到上一次提交后的状态
git checkout -- demo.js  回滚,还原代码,status为空为止

# git merge

# git tag打标签
git tag -a v1.0  给这个项目的版本标注一个v1.0标签





# 分支管理

HEAD相当于一个指针,指向当前版本
git branch dev 新建dev分支
git branch -d dev 删除dev分支
git checkout dev 切换分支
git checkout master 切换回主分支
git merge dev 把dev分支合并到了主分支上


```















# GitHub远程管理

Github网站
branches: clone代码时候有一个Tag可以选择版本和分支
Repository: 仓库的意思,即你的项目,你想在 GitHub 上开源一个项目,那就必须要新建一个 Repository ,如果你开源的项目多了,你就拥有了多个 Repositories 。 
Issue: 问题的意思,举个例子,就是你开源了一个项目,别人发现你的项目中有bug,或者哪些地方 做的不够好,他就可以给你提个 Issue ,即问题,提的问题多了,也就是 Issues ,然后你看 到了这些问题就可以去逐个修复,修复ok了就可以一个个的 Close 掉。 
Star 这个好理解,就是给项目点赞,但是在 GitHub 上的点赞远比微博、知乎点赞难的多,如果你 有一个项目获得100个star都算很不容易了! 
Fork 这个不好翻译,如果实在要翻译我把他翻译成分叉,什么意思呢?你开源了一个项目,别人 想在你这个项目的基础上做些改进,然后应用到自己的项目中,这个时候他就可以 Fork 你的 项目,这个时候他的 GitHub 主页上就多了一个项目,只不过这个项目是基于你的项目基础 (本质上是在原有项目的基础上新建了一个分支,分支的概念后面会在讲解Git的时候说 到),他就可以随心所欲的去改进,但是丝毫不会影响原有项目的代码与结构。 
Pull Request  拉回请求 发起请求,这个其实是基于 Fork 的,还是上面那个例子,如果别人在你基础上做了改进,后 来觉得改进的很不错,应该要把这些改进让更多的人收益,于是就想把自己的改进合并到原 有项目里,这个时候他就可以发起一个 Pull Request(简称PR) ,原有项目创建人就可以收 到这个请求,这个时候他会仔细review你的代码,并且测试觉得OK了,就会接受你的PR,这 个时候你做的改进原有项目就会拥有了。 
Watch这个也好理解就是观察,如果你 Watch 了某个项目,那么以后只要这个项目有任何更新,你都会第一时间收到关于这个项目的通知提醒。 
Gist有些时候你没有项目可以开源,只是单纯的想分享一些代码片段,那这个时候 Gist 就派上用 场了! 


```bash
ssh-keygen -t rsa -C "邮箱@地址.com"
这个命令会在win://~/.ssh/id_rsa/目录下生成好多文件
```
在github设置里面,有一个"SSH and GPG keys"选项
把生成好的pub公钥上传到github（打开编辑器复制进去）



```bash
# git remote关联/取消 远程地址
https://www.runoob.com/git/git-remote-repo.html
git remote add origin git@github.com:地址
git remote rm origin 删除了与远程库的连接

# git clone
git clone repo  克隆仓库
git clone repo dir  克隆仓库到本地dir目录



例如：
git clone git://github.com/schacon/grit.git
执行后,会创建一个grit目录,其中还有.git目录
git clone git://github.com/schacon/grit.git mygrit
执行后,会创建一个mygrit目录,其中还有.git目录




克隆自己的代码可以直接push,无需关联
在工作区修改了内容之后
记得git init,初始化了才能关联


# git pull下载远端的文件
git pull origin master





# git push上传代码文件
上传之前记得add和commit
本地的代码上传到远端
git push origin master
```



# GitLab
搭建自己的服务器




# Gitee





# IDEA集成Git


# 搭建Git服务器














# 许可证
如何选择许可证 https://choosealicense.com
许可证列表 https://choosealicense.com/licenses/
许可证列表 https://opensource.org/licenses/alphabetical

Apache License 2.0
GNU GPL（General Public License 通用公共许可证）
MIT License
BSD
Eclipse Public License 2.0
Mozilla Public License 
Boost Software License
The Unlicense

Apache: Apache Licence是著名的非盈利开源组织Apache采用的协议。该协议和BSD类似,同样鼓励代码共享和尊重原作者的著作权,同样允许代码修改,再发布（作为开源或商业软件）。需要满足的条件也和BSD类似： 
1需要给代码的用户一份Apache Licence 
2如果你修改了代码,需要在被修改的文件中说明。 
3在延伸的代码中（修改和有源代码衍生的代码中）需要带有原来代码中的协议,商标,专利声明和其他原来作者规定需要包含的说明。 
4如果再发布的产品中包含一个Notice文件,则在Notice文件中需要带有Apache Licence。你可以在Notice中增加自己的许可,但不可以表现为对Apache Licence构成更改。 
Apache Licence也是对商业应用友好的许可。使用者也可以在需要的时候修改代码来满足需要并作为开源或商业产品发布/销售。 
英文原文：http://www.apache.org/licenses/LICENSE-2.0.html

GPL: 在自由软件所使用的各种许可证之中,最为人们注意的也许是通用性公开许可证(General Public License,简称GPL)。
GPL同其它的自由软件许可证一样,许可社会公众享有：运行、复制软件的自由,发行传播软件的自由,获得软件源码的自由,改进软件并将自己作出的改进版本向社会发行传播的自由。 
GPL还规定：只要这种修改文本在整体上或者其某个部分来源于遵循GPL的程序,该修改文本的 整体就必须按照GPL流通,不仅该修改文本的源码必须向社会公开,而且对于这种修改文本的流通不准许附加修改者自己作出的限制。因此,一项遵循GPL流通 的程序不能同非自由的软件合并。GPL所表达的这种流通规则称为copyleft,表示与copyright(版权)的概念“相左”。
GPL协议最主要的几个原则：
1、确保软件自始至终都以开放源代码形式发布,保护开发成果不被窃取用作商业发售。任何一套软 件,只要其中使用了受 GPL 协议保护的第三方软件的源程序,并向非开发人员发布时,软件本身也就自动成为受 GPL 保护并且约束的实体。也就是说,此时它必须开放源代码。 
2、GPL 大致就是一个左侧版权（Copyleft,或译为“反版权”、“版权属左”、“版权所无”、“版责”等）的体现。你可以去掉所有原作的版权 信息,只要你保持开源,并且随源代码、二进制版附上 GPL 的许可证就行,让后人可以很明确地得知此软件的授权信息。GPL 精髓就是,只要使软件在完整开源 的情况下,尽可能使使用者得到自由发挥的空间,使软件得到更快更好的发展。 
3、无论软件以何种形式发布,都必须同时附上源代码。例如在 Web 上提供下载,就必须在二进制版本（如果有的话）下载的同一个页面,清楚地提供源代码下载的链接。如果以光盘形式发布,就必须同时附上源文件的光盘。 
4、开发或维护遵循 GPL 协议开发的软件的公司或个人,可以对使用者收取一定的服务费用。但还是一句老话——必须无偿提供软件的完整源代码,不得将源代码与服务做捆绑或任何变相捆绑销售。

MIT: MIT许可证之名源自麻省理工学院（Massachusetts Institute of Technology, MIT）,又称「X条款」（X License）或「X11条款」（X11 License） 
MIT内容与三条款BSD许可证（3-clause BSD license）内容颇为近似,但是赋予软体被授权人更大的权利与更少的限制。 
被授权人有权利使用、复制、修改、合并、出版发行、散布、再授权及贩售软体及软体的副本。 
被授权人可根据程式的需要修改授权条款为适当的内容。 

在软件和软件的所有副本中都必须包含版权声明和许可声明。 
此授权条款并非属copyleft的自由软体授权条款,允许在自由/开放源码软体或非自由软体（proprietary software）所使用。 
此亦为MIT与BSD（The BSD license, 3-clause BSD license）本质上不同处。 
MIT条款可与其他授权条款并存。另外,MIT条款也是自由软体基金会（FSF）所认可的自由软体授权条款,与GPL相容。 
协议英文原文：http://www.opensource.org/licenses/mit-license.php

BSD: 开源协议是一个给于使用者很大自由的协议。可以自由的使用,修改源代码,也可以将修改后的代码作为开源或者专有软件再发布。当你发布使用了BSD协议的代码,或者以BSD协议代码为基础做二次开发自己的产品时,需要满足三个条件：
如果再发布的产品中包含源代码,则在源代码中必须带有原来代码中的BSD协议。
如果再发布的只是二进制类库/软件,则需要在类库/软件的文档和版权声明中包含原来代码中的BSD协议。
不可以用开源代码的作者/机构名字和原来产品的名字做市场推广。
BSD代码鼓励代码共享,但需要尊重代码作者的著作权。BSD由于允许使用者修改和重新发布代码,也允许使用或在BSD代码上开发商业软件发布和销 售,因此是对商业集成很友好的协议。很多的公司企业在选用开源产品的时候都首选BSD协议,因为可以完全控制这些第三方的代码,在必要的时候可以修改或者 二次开发。

EPL

MPL: 是The Mozilla Public License的简写,是1998年初Netscape的 Mozilla小组为其开源软件项目设计的软件许可证。MPL许可证出现的最重要原因就是,Netscape公司认为GPL许可证没有很好地平衡开发者对 源代码的需求和他们利用源代码获得的利益。同著名的GPL许可证和BSD许可证相比,MPL在许多权利与义务的约定方面与它们相同（因为都是符合OSIA 认定的开源软件许可证）。但是,相比而言MPL还有以下几个显著的不同之处:
MPL虽然要求对于经MPL许可证发布的源代码的修改也要以MPL许可证的方式再许可出来,以保证其他人可以在MPL的条款下共享源代码。但是,在MPL 许可证中对“发布”的定义是“以源代码方式发布的文件”,这就意味着MPL允许一个企业在自己已有的源代码库上加一个接口,除了接口程序的源代码以MPL 许可证的形式对外许可外,源代码库中的源代码就可以不用MPL许可证的方式强制对外许可。这些,就为借鉴别人的源代码用做自己商业软件开发的行为留了一个 豁口。 
MPL许可证第三条第7款中允许被许可人将经过MPL许可证获得的源代码同自己其他类型的代码混合得到自己的软件程序。 
对软件专利的态度,MPL许可证不像GPL许可证那样明确表示反对软件专利,但是却明确要求源代码的提供者不能提供已经受专利保护的源代码（除非他本人是 专利权人,并书面向公众免费许可这些源代码）,也不能在将这些源代码以开放源代码许可证形式许可后再去申请与这些源代码有关的专利。 
对源代码的定义: 而在MPL（1.1版本）许可证中,对源代码的定义是:“源代码指的是对作品进行修改最优先择 取的形式,它包括:所有模块的所有源程序,加上有关的接口的定义,加上控制可执行作品的安装和编译的‘原本’（原文为‘Script’）,或者不是与初始 源代码显著不同的源代码就是被源代码贡献者选择的从公共领域可以得到的程序代码。” 
MPL许可证第3条有专门的一款是关于对源代码修改进行描述的规定,就是要求所有再发布者都得有一个专门的文件就对源代码程序修改的时间和修改的方式有描述。
英文原文：http://www.mozilla.org/MPL/MPL-1.1.html







# 五种开源协议的比较

五种开源协议的比较(BSD,Apache,GPL,LGPL,MIT)
当Adobe、Microsoft、Sun等一系列巨头开始表现出对”开源”的青睐时,”开源”的时代即将到来！
最初来自：sinoprise.com/read.php?tid-662-page-e-fpage-1.html（遗憾的是这个链接已经打不开了）,我基本未改动,只是进行了一些排版和整理。
参考文献：http://www.fsf.org/licensing/licenses/

现今存在的开源协议很多,而经过Open Source Initiative组织通过批准的开源协议目前有58种（http://www.opensource.org/licenses/alphabetical）。我们在常见的开源协议如BSD, GPL, LGPL,MIT等都是OSI批准的协议。如果要开源自己的代码,最好也是选择这些被批准的开源协议。
这里我们来看四种最常用的开源协议及它们的适用范围,供那些准备开源或者使用开源产品的开发人员/厂家参考。
BSD开源协议 original BSD license http://www.fsf.org/licensing/licenses/index_html#OriginalBSD
FreeBSD license http://www.freebsd.org/copyright/freebsd-license.html
Original BSD license http://www.xfree86.org/3.3.6/COPYRIGHT2.html#6)

BSD开源协议是一个给于使用者很大自由的协议。基本上使用者可以”为所欲为”,可以自由的使用,修改源代码,也可以将修改后的代码作为开源或者专有软件再发布。

但”为所欲为”的前提当你发布使用了BSD协议的代码,或则以BSD协议代码为基础做二次开发自己的产品时,需要满足三个条件：

1. 如果再发布的产品中包含源代码,则在源代码中必须带有原来代码中的BSD协议。
2. 如果再发布的只是二进制类库/软件,则需要在类库/软件的文档和版权声明中包含原来代码中的BSD协议。
3. 不可以用开源代码的作者/机构名字和原来产品的名字做市场推广。

BSD 代码鼓励代码共享,但需要尊重代码作者的著作权。BSD由于允许使用者修改和重新发布代码,也允许使用或在BSD代码上开发商业软件发布和销售,因此是对 商业集成很友好的协议。而很多的公司企业在选用开源产品的时候都首选BSD协议,因为可以完全控制这些第三方的代码,在必要的时候可以修改或者二次开发。

Apache Licence 2.0 Apache License, Version 2.0 http://www.apache.org/licenses/LICENSE-2.0、Apache License, Version 1.1 http://www.apache.org/LICENSE-1.1、Apache License, Version 1.0 http://www.apache.org/LICENSE-1.0

Apache Licence是著名的非盈利开源组织Apache采用的协议。该协议和BSD类似,同样鼓励代码共享和尊重原作者的著作权,同样允许代码修改,再发布（作为开源或商业软件）。需要满足的条件也和BSD类似：

1. 需要给代码的用户一份Apache Licence
2. 如果你修改了代码,需要再被修改的文件中说明。
3. 在延伸的代码中（修改和有源代码衍生的代码中）需要带有原来代码中的协议,商标,专利声明和其他原来作者规定需要包含的说明。
4. 如果再发布的产品中包含一个Notice文件,则在Notice文件中需要带有Apache Licence。你可以在Notice中增加自己的许可,但不可以表现为对Apache Licence构成更改。

Apache Licence也是对商业应用友好的许可。使用者也可以在需要的时候修改代码来满足需要并作为开源或商业产品发布/销售。
GPL GNU General Public License http://www.fsf.org/licensing/licenses/gpl.html

我们很熟悉的Linux就是采用了GPL。GPL协议和BSD, Apache Licence等鼓励代码重用的许可很不一样。GPL的出发点是代码的开源/免费使用和引用/修改/衍生代码的开源/免费使用,但不允许修改后和衍生的代 码做为闭源的商业软件发布和销售。这也就是为什么我们能用免费的各种linux,包括商业公司的linux和linux上各种各样的由个人,组织,以及商 业软件公司开发的免费软件了。

GPL协议的主要内容是只要在一个软件中使用(”使用”指类库引用,修改后的代码或者衍生代码)GPL 协议的产品,则该软件产品必须也采用GPL协议,既必须也是开源和免费。这就是所谓的”传染性”。GPL协议的产品作为一个单独的产品使用没有任何问题,还可以享受免费的优势。

由于GPL严格要求使用了GPL类库的软件产品必须使用GPL协议,对于使用GPL协议的开源代码,商业软件或者对代码有保密要求的部门就不适合集成/采用作为类库和二次开发的基础。

其它细节如再发布的时候需要伴随GPL协议等和BSD/Apache等类似。

LGPL GNU Lesser General Public License http://www.fsf.org/licensing/licenses/lgpl.html
LGPL是GPL的一个为主要为类库使用设计的开源协议。和GPL要求任何使用/修改/衍生之GPL类库的的软件必须采用GPL协议不同。LGPL 允许商业软件通过类库引用(link)方式使用LGPL类库而不需要开源商业软件的代码。这使得采用LGPL协议的开源代码可以被商业软件作为类库引用并 发布和销售。

但是如果修改LGPL协议的代码或者衍生,则所有修改的代码,涉及修改部分的额外代码和衍生的代码都必须采用LGPL协议。因此LGPL协议的开源 代码很适合作为第三方类库被商业软件引用,但不适合希望以LGPL协议代码为基础,通过修改和衍生的方式做二次开发的商业软件采用。

GPL/LGPL都保障原作者的知识产权,避免有人利用开源代码复制并开发类似的产品
MIT MIT http://www.opensource.org/licenses/mit-license.php

MIT是和BSD一样宽范的许可协议,作者只想保留版权,而无任何其他了限制.也就是说,你必须在你的发行版里包含原许可协议的声明,无论你是以二进制发布的还是以源代码发布的.
常见的开放源代码许可证类型 https://blog.csdn.net/fengyuruhui/article/details/1791842






