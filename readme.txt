1. 基本
	初始化仓库：git init
	添加文件到git仓库：
		a.	git add {fileName}
		b.	git commit -m "提交备注信息"
	删除文件并且提交至版本库：
		git rm {fileName}
		rm {fileName}
		git commit -m "删除了{fileName}"
		
	查看仓库当前状态：git status
	查看文件修改内容：git diff {fileName}   附加： git diff HEAD -- {fileName} 查看工作区和版本库里面新版本的区别，HEAD表示版本库最新版本
	查看仓库提交日志：git log	美化日志结果显示： git log --pretty=oneline
	文件跳转到知道版本：
		Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，上一个版本就是 HEAD^，上上一个版本就是HEAD^^，当然往上100 个版本写100个^比较容易数不过来， 所以写成HEAD~100
		如：git reset --hard HEAD^   跳转到上一个版本
			git reset --hard 3628164   调到指定commit id版本，commit id填写前面一部分即可
	Git提供了一个命令git reflog用来记录你的每一次命，一般用于 git reset --hard 到较低版本时候，如果像再回到之前的新版本，就需要通过这个查看开始最新的commit id然后确定跳转至哪个版本。

	git分为：工作区，暂存区，版本库
		工作区, 就是我们项目编辑的目录
		暂存区, 就是执行git add后会将工作区文件提交至暂存区。
		版本库, 就是执行git commit后将暂存区提交至版本库
		
		git checkout -- {fileName} 把{fileName}文件在工作区的修改全部撤销, 文件如果之前有提交工作区(git add)就与工作区相同，否则就是与版本库相同。
	
2. 远程仓库(gitbut)
	生成ssh-key
	ssh-keygen -t rsa -C "youremail@example.com" 
	之后会在系统盘用户目录下出现.ssh目录（X:\Users\Aukey\.ssh）⾥里⾯面有id_rsa和id_rsa.pub两个⽂文 件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可 以放⼼心地告诉任何人。 
	登陆GitHub，打开“Account settings”，“SSH Keys”⻚页⾯面： 然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
	
	本地仓库与远程仓库命令：
	git remote add origin git@github.com:michaelliao/learngit.git 
	请千万注意，把上面的michaelliao替换成你自己的GitHub账户名，否则你在本地关联的就是我的远程库。关联没有问题，但是你以后推送是推不上去的，因为你的SSH Key公钥不在我的账户列表中。 
	https形式：
	git remote add origin https://github.com/iblilife/iblilife.git 
	添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。 
	下一步就是推送本地仓库内容只远程仓库：
	git push -u origin master 
	把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
	由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的 master分支内容推送的远程新的master分支，还会把本地的master分⽀支和远程的master 分支关联起来，在以后的推送或者拉取时就可以简化命令。 
	git push origin master 
	
	
3. 分支相关	
	查看所有分支：git branch					带*符号表示当前分支
	创建分支：git branch {Branch Name}			
	切换分支：git checkout {Branch Name}
	创建+切换分支：git checkout -d {Branch Name}
	合并分支：git merge {Branch Name}
	删除分支：git branch -d {Branch Name}
