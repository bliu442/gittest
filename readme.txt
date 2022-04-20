学习使用git，在终端使用命令操作git

ctrl + · 打开终端 ·是键盘上esc下面的那个
ctrl + Shift + · 推出终端
E325错误 git在指令意外中断时，一般会有一个缓存的机制，它会记住上次中断的问题。在下次进入vim指令时，如果很重要的中断一般会提示你前面有某个操作不当或者没有结束
解决：删除根目录下的.git文件夹.COMMIT_EDITMSG.swp     rm .git/.COMMIT_EDITMSG.swp 
git项目初次push error: failed to push some refs to 'https://github.com/bliu442/gittest.git'
解决1.git push -f origin master强制将本地文件推送至远程，这样会将远程仓库的已有的文件清掉 
2.git pull origin master –allow-unrelated-histories 使用此命令告诉 git 允许不相关历史合并 这样就能把远程文件拉取回来。执行此命令后会有一个提示，要求说明为何要讲两个不相关的分支合并，输入信息后保存即可。

git add +文件名/文件夹名 将该文件/文件夹 所有改动暂存
git commit -m "版本说明" 将当前暂存区提交到本地库 每次使用git commit 命令我们都会在本地版本库生成一个40位的哈希值，这个哈希值也叫commit-id
git commit --amend 追加提交，它可以在不增加一个新的commit-id的情况下将新修改的代码追加到前一次的commit-id中
windows下 git commit --amend后进入vim编辑器，c进入插入模式，Esc推出插入模式，ZZ保存，或者直接使用git commit --amend -m "版本说明"
git reset --hard HEAD^ 回到前一个版本 其中HEAD表示当前最新版本【请记死】，HEAD^表示当前版本的前一个版本，HEAD^^表示当前版本的前前个版本，也可以使用HEAD~1表示当前版本的前一个版本，HEAD~100表示当前版本的前100版本。
git reset --hard 版本号 回到指定版本，上一个命令只能回到之前的版本，如果想要再回到后面的版本，就需要使用git reset --hard 版本号commit-id前7位
git reflog 如果从之前的版本看不到后面的版本的版本号，使用该命令可以查看操作记录 
git checkout –- 文件 来丢弃该文件工作区的改动
git reset HEAD file 把暂存区的修改撤销掉

场景1:当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout –- 文件
场景2:当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步：
第一步用命令git reset HEAD – file,就回到了场景1,
第二步按场景1操作。
场景3:已经提交了不合适的修改到版本库时，想要撤销本次提交，使用版本回退一节。

git log  查看版本记录 (HEAD -> master)所在行是当前版本
Q退出git log界面

分支操作
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>
解决冲突:分支对文件进行更改，master对该文件也进行了更改，git无法进行快速合并

远程操作
git remote add origin https://github.com/bliu442/gittest.git 增加了与远程仓库gittest关联
git remote remove gittest 移除远端仓库关联
git push -u origin master 将本地仓库内容推送到远端仓库(-u 表示第一次推送master分支的所有内容，后面再推送就不需要-u了)，跟commit的区别在于一个是提交到本地仓库，一个是提交到远程仓库
git pull origin master 把远程分支master上的代码下载并合并到本地所在分支

这是第一行
这是第二行

这是第三行
这是第四行