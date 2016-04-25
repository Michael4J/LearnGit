Git Study
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
	注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。
	
$ git init     					初始化一个Git仓库，使用git init命令。(当前文件夹作为仓库)
添加文件到Git仓库，分两步：
$ git add <fileName>				•第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
$ git commit -m "init file"			•第二步，使用命令git commit，完成。

文件修改后可以查看变化：
$ git status					•要随时掌握工作区的状态，使用git status命令。
$ git diff <fileName>				•如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
然后再：
$ git add <fileName>
$ git commit -m "modify file"

$ git log					git log命令显示从最近到最远的提交日志
$ git log --pretty=oneline
$ git reset --hard HEAD^			回退到上一个版本
	在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
$ git reflog					git reflog用来记录你的每一次命令
$ git reset --hard ccd9ae6			回退到commit_id 为ccd9ae6的版本

工作区（Working Directory）:就是你在电脑里能看到的目录，比如我的Test文件夹就是一个工作区
版本库（Repository）:工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

$ git checkout -- <fileName>			将当前暂存区的文件覆盖到工作区
$ git reset HEAD <fileName>			将版本库的文件覆盖到暂存区
$ git rm <fileName>				命令git rm用于删除一个文件。

远程仓库Repository
1.本地到远程
$ git remote add origin git@github.com:Michael4J/LearnGit.git		关联远程仓库
$ git push -u origin master			第一次推送master分支的所有内容（我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。）
$ git push origin master			此后推送更新。
2.远程到本地
$ git clone git@github.com:Michael4J/Hello-World.git			克隆远程仓库
$ git clone https://github.com/Michael4J/Hello-World.git		Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

分支管理
$ git checkout -b dev				创建dev分支，然后切换到dev分支
git checkout命令加上-b参数表示创建并切换，相当于以下两条命令：
$ git branch dev				创建dev分支
$ git checkout dev				切换到dev分支

$ git branch					git branch命令会列出所有分支，当前分支前面会标一个*号

$ git checkout master
$ git merge dev					git merge命令用于合并指定分支到当前分支。（dev-->master）
$ git branch -d dev				删除dev分支

Bug分支
软件开发中，bug就像家常便饭一样。有了bug就需要修复，在Git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。
当你接到一个修复一个代号101的bug的任务时，很自然地，你想创建一个分支issue-101来修复它，但是，等等，当前正在dev上进行的工作还没有提交。
并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？
幸好，Git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作。
$ git stash					将工作现场储藏起来，查看工作区，就是干净的。
修改完bug后又回来继续工作：
$ git stash list				git stash list查看储藏的工作现场
现在恢复工作现场：
$ git stash pop					恢复的同时把stash内容也删了
	还有一种方法：先$ git stash apply恢复，stash内容并不删除，需要用$ git stash drop来删除。
