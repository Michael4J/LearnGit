Git Study
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
	注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。
	
$ git init     						初始化一个Git仓库，使用git init命令。(当前文件夹作为仓库)
添加文件到Git仓库，分两步：
$ git add <fileName>				•第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
$ git commit -m "init file"			•第二步，使用命令git commit，完成。

文件修改后可以查看变化：
$ git status						•要随时掌握工作区的状态，使用git status命令。
$ git diff <fileName>				•如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
然后再
$ git add <fileName>
$ git commit -m "modify file"

$ git log							git log命令显示从最近到最远的提交日志
$ git log --pretty=oneline
$ git reset --hard HEAD^			回退到上一个版本
	在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
$ git reflog						git reflog用来记录你的每一次命令
$ git reset --hard ccd9ae6			回退到commit_id 为ccd9ae6的版本

工作区（Working Directory）
就是你在电脑里能看到的目录，比如我的Test文件夹就是一个工作区
版本库（Repository）
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

$ git checkout -- <fileName>		将当前暂存区的文件覆盖到工作区
$ git reset HEAD <fileName>			将版本库的文件覆盖到暂存区
$ git rm <fileName>					命令git rm用于删除一个文件。