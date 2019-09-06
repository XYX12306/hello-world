git
git config --global user.name "XYX12306"
git config --global user.email "2669599387@qq.com"
mkdir learngit
cd learngit
pwd										命令用于显示当前目录
git init								把当前目录变成Git可以管理的仓库
touch .gitignore						创建.gitignore文件
ls
ls -ah									显示隐藏的.git等目录
git add readme.txt						把工作区的文件添加到本地版本库的暂存区
git commit -m "wrote a readme file"		把本地版本库的暂存区的文件提交到本地版本库的当前分支
git status								查看仓库当前的状态
git diff								比较文件修改前后的变化，
git diff HEAD -- readme.txt				查看工作区和版本库里面最新版本的区别
git log	(--pretty=oneline)				命令行窗口还没关闭时，查看提交历史记录(简化)
git reflog								命令行窗口还没关闭后重新打开，查看命令历史
git reset --hard HEAD^					当前版本回退到上一个版本，再用git log看不到最新版本
git reset --hard HEAD^^					当前版本回退到上上个版本
git reset --hard HEAD~100				当前版本回退到前100个版本
git reset --hard <commit id>			当前版本回退到指定commit id的版本						
git reset HEAD <file>					把暂存区的修改撤销掉，把暂存区的修改回退到工作区
cat readme.txt							查看文件的内容
git checkout -- <file>					丢弃工作区/本地版本库的暂存区的修改，让这个文件回到最近一次git commit或git add时的状态
										用本地版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”
rm <file>								删除工作区的文件
git rm <file>							删除本地版本库的当前分支的文件，再用git commit确认
ssh-keygen -t rsa -C "2669599387@qq.com"创建SSH Key
git remote add origin git@github.com:XYX12306/learngit.git本地关联的就是远程库的learngit.git仓库
git push -u origin master				把本地版本库的所有文件推送到远程库
										-u：远程库为空，第一次推送时，把本地的master分支内容推送和关联远程新的master分支
git push origin master/<tagname>		把本地master分支/标签的最新修改推送至GitHub的origin分支
git push origin --tags					一次性推送全部尚未推送到远程的本地标签
git push origin :refs/tags/<tagname>	删除远程的标签（需先删除本地的标签）
git pull								把最新的提交从origin/dev抓下来（要先指定本地dev分支与远程origin/dev分支的链接）
git clone git@github.com:XYX12306/gitskills.git把远程库gitskills.git克隆到本地版本库
git checkout -b dev						创建dev分支并切换到dev分支
git checkout -b dev origin/dev			创建远程origin的dev分支到本地，创建本地dev分支
git branch dev							创建dev分支
git branch -d dev						须在合并后，再进行删除dev分支
git branch -D dev						丢弃一个没有被合并过的分支，强行删除dev分支
git branch								查看当前分支
git branch --set-upstream-to=origin/dev dev指定本地dev分支与远程origin/dev分支的链接
git checkout dev						切换到dev分支
git merge dev							合并指定分支到当前分支，看不出来曾经做过合并
git merge --no-ff -m "merge with no-ff" dev合并指定分支到当前分支并禁用Fast forward，
										合并后的历史有分支，能看出来曾经做过合并
git switch -c dev						创建并切换到新的dev分支
git switch master						直接切换到已有的master分支
git log --graph --pretty=oneline --abbrev-commit查看分支合并图
git stash								把当前工作现场“储藏”起来
git stash pop							恢复的同时把stash内容也删除
git stash apply							仅是恢复，stash内容并不删除
git stash apply stash@{0}				恢复指定的stash
git stash drop							删除stash内容
git stash list							查看stash
git cherry-pick <commit id>				复制一个特定的提交到当前分支
git remote								查看远程库的信息
git remote -v							显示远程库更详细的信息
git remote remove origin				取消当前版本库绑定的远程库
git rebase								把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了
git tag <tagname> (<commit id>)			在当前（指定ID）分支上创建一个新的标签
git tag -d <tagname>					删除标签
git tag -a <tagname> -m "<explation>" <commit id>创建带有说明的标签，用-a指定标签名，-m指定说明文字
git tag									查看标签，按字母排序列出
git show <tagname>						查看标签信息