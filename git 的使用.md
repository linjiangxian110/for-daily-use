# git 安装使用教程

 1. 官网下载 git ；
 2. git 下载成功后打开终端，输入 `git -v`,查询版本信息，如果可以看到版本信息说明成功；
    - 打开 git,输入 `git config --global user.name "name"`, name 是你起的名字；
	- 输入 `git config --global user.email "email"`, eamil 是你的邮箱；
	- （3.4 步骤的配置在于后续对仓库内容进行修改时候，方便记录是谁修改了什么内容）

# git 的工作区域和文件状态

git 的本地数据管理分为三个区域，包括工作区，暂存区和本地仓库；

1. 工作区（Working Directoy）,也就是自己电脑上的目录；
	   使用 `ls` 命令可以查看工作区内容；
1. 暂存区（Staging Area）,是一种临时储存区域，用于保存即将提交到 git 仓库的修改内容；
	   使用 `git ls-files` 可以查看暂存区的内容； 
1. 本地仓库（Local Repository）就是使用 `git init` 创建的本地仓库；用于存储代码和版本信息；
	![[Pasted image 20240921163458.png|350]]

# git 文件的状态：

1. 未跟踪：我们新创建的还没有被 git 管理起来的文件；
2. 未修改：已经被 git 管理起来，但是文件的内容没有变化，没有被修改过 ；
3. 已修改：已经修改过的文件，但是没有添加到暂存区；
4. 已暂存：修改后并且添加到暂存区的文件；

![[Pasted image 20240921164522.png|350]]

`git add .` 用于把当前文件夹下的所有文件都添加到暂存区内，这里的 `.` 表示当前目录；
`git log` 命令可用于查看提交记录；按下 `q` 键可以退出；
`git log --oneline` 可以用于查看简洁的提交记录；
`git commit -m "<comment>"` 用于提交文件，双引号用于写提交信息，写备注；我们规定的格式为“`docs:添加了离散数学课程”`

# git reset 的使用 

用于撤销之前的修改内容或者回退到之前的某个版本；
1. `git reset --soft` ，保留工作区和暂存区的修改内容；
2. `git reset --hard` ，~~
3. `git reset --mixed

`git reflog` 可以查看我们操作的所有历史记录；

![[Pasted image 20240921170304.png|500]]

# git diff 使用介绍

![[Pasted image 20240921171734.png|500]]

`git diff` 用于查看工作区和暂存区之间的差异；
![[Pasted image 20240921171835.png|500]]

![[Pasted image 20240921172400.png|250]]

第一行显示的是发生修改的文件.....下面红色的表示删除的内容，绿色表示添加的内容；

`git diff HEAD` 用于比较工作区和版本库之间的差异；
`git diff ID1 ID2` 用于比较两个版本之间的差异：
![[Pasted image 20240921172926.png|700]]

`HEAD` 指向的是分支的最新提交节点，经常用于比较版本差异，比如： `git diff ID1 HEAD` 就是比较 ID 为“ID1”的的版本和最新版本的差异；

`HEAD~` 可以用于表示上一个版本，因此最近两个版本之间的比较可以写作 `git diff HEAD HEAD~`,
`git diff HEAD HEAD^` 具有同样的作用；

此外，`git diff HEAD HEAD~X`,X 用于填写数字，比如 `git diff HEAD HEAD~2` 表示提交之前的倒数第二个版本,就是倒数第三个版本；比如下面的 `git diff HEAD~3 HEAD`,指向版本“ commit3”（HEAD~3）和“commit4”(HEAD) 的比较。

![[Pasted image 20240921173857.png|700]]

![[Pasted image 20240921180842.png|700]]

`git remote -v` 用于查看本地仓库连接的远程仓库的别名和地址；如下面的两个远程仓库别名都叫做 origin; 

![[Pasted image 20240921181851.png]]

`git pull ` 用于拉取远程仓库的文件，这里仓库的名称和分支的名称省略了，这时默认拉取仓库别名为 origin 的 main 分支；

![[Pasted image 20240921182225.png]]
# 这是在github 网站的编辑
