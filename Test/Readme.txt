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