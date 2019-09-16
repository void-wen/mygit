***

# 基础

git init 
git add files添加文件到仓库
git commit -m “文件说明” 提交文件   git commit -amend提交修改补充
git status 查看仓库状态
git diff files 查看修改内容
git log 查看版本日志（git log --pretty=oneline）
git reset --hard HEAD^ 回到上一个版本（HEAD^^上两个 HEAD~100前100个）或者 git reset --hard 版本号前几位
cat files 查看文件内容
git reflog 查看版本记录
git checkout -- files恢复文件
git rm 删除文件
<u>`$ git log --graph --pretty=oneline --abbrev-commit`</u>



# 分支

查看分支：`git branch`
创建分支：```git branch <name>```
切换分支：```git checkout <name>```
创建+切换分支：```git checkout -b <name>```
合并某分支到当前分支：```git merge <name>```
删除分支：```git branch -d <name>```
用`git log --graph`命令可以看到分支合并图。

>*合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来*
>*曾经做过合并，而fast forward合并就看不出来曾经做过合并。*
>*`$ git merge --no-ff -m "merge with no-ff" dev`*
>*先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。*
>
>**一是用git stash apply恢复，但是恢复后，stash内容并不删除，**
>**你需要用git stash drop来删除；**
>**另一种方式是用git stash pop，恢复的同时把stash内容也删了**
>**git stash list**
>**如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。**

###### 多人协作
查看远程库信息，使用`git remote -v`
本地新建的分支如果不推送到远程，对其他人就是不可见的；
从本地推送分支，使用`git push origin branch-name，`如果推送失败，先用git pull抓取远程的新提交；
在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name；`
从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。

# 远程仓库

要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git；`
关联后，使用命令`git push -u origin master第一次`推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；
要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。

`git clone git@github.com:michaelliao/gitskills.git`

<!--（远程仓库克隆必须是一个完整的仓库，而不能选择单独的文件）-->



