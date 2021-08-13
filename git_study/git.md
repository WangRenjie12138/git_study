## 安装

### 配置信息

```bash
$git config --global user.name "Wang Renjie"
$git config --global user.email "857638220@qq.com"
```

### 创建版本库

```bash
$git init    # init git, transfer the folder to git respository

$git add git_study  #put the folder into the resposity
				  #when there is no message after the operation,it means success
				  
$git commit -m "create a git_study note" #we add some message

```

### 时光机穿梭.jpg

#### 版本回退

```bash
$git status     #get git status

$git diff      #we can get its use by its name

$ git status
On branch master
nothing to commit, working tree clean

```

```bash
$git log (--pretty oneline)           #show the log   ()option,make the log all in one line
55df8c1bc0335753227b47ea00b07d4590cd5a1e create and write a note about git     #55dfbalabala  is commit id

$git reset --hard HEAD^           #back to the last version   HEAD^^ means last last version,   HEAD~100  last 100 version

$git reset --hard 55df8           #back to the version whose commit id is 55df8c etc

#rollback is fast because git only update the pointer into different version
```

![image-20210812163929600](git.assets/image-20210812163929600.png)

```bash
# if we rollback and want to rollback again, we can use *git feflog* to get our command history the we can get the commit id.
$git reflog
```



#### 工作区和暂存区

Working Directory and Repository

git add command copy the file into the stage (暂存区) of Repository, we can add many times.

the  commit the update into the master(分支) of  respository.



#### 管理修改

git add changes into stage then commit into master

<u>*git manage the changes instead of files.*</u>



#### 撤销修改

```bash
#drop changes in work directory
$git checkout -- file     
#drop the update in working directory
	#if the update has not been put into stage, then it will withdraw to the respository version.
	#if the update has been put into stage and update again, it will withdraw to stage version.
#To sum up, file will return to the last git commit/add version
```

```bash
#drop changes in stage
$git reset HEAD file        #withdraw changes in stage to work directory
$git checkout -- file
```



```bash
git 最新更新
从暂存区恢复工作区，
git resotre --worktree readme.txt

从 master 恢复暂存区 
git restore --staged readme.txt

从 master 同时恢复工作区和暂存区
git restore --source=HEAD --staged --worktree readme.txt
```



#### Delete file

```bash
#delete file in respository
git rm file
git commit -m "delete file"

git rm file
git resotre 
```





### 远程仓库

```bash
$ssh-keygen -t rsa -C "857638220@qq.com"
```

创建完成后可以在用户主目录   /user/windows10/.ssh看到id_rsa和id_rsa.pub两个文件

前者是私钥，后者是公钥。



配置GitHub

在设置中add SSH Key，粘贴id_rsa.pub文件

为了确认是本人推送的分支。

#### 添加远程仓库

先在GitHub上创建远程仓库。

```bash
git remote add origin git@github.com:WangRenjie12138/git_study.git
git push -u origin master

#使用git push 命令，将master分支推送到远程。
#因为远程库是空的，因此加上了-u参数，git会将本地的master分支内容推送到远程新的master分支，并且将两者关联起来。

#此后可以直接使用
git push origin master
```

#### 删除远程库

```bash
git remote -v     #用于查看远程库信息
git remote rm origin    #根据名字删除了origin

#此处删除为解除绑定，物理删除的话则需要登录GitHub进行删除
```



#### 从远程库克隆下来

```bash
git clone git@github.com:WangRenjie12138/git_study.git
```





### 分支管理

协作过程中每个人可以创建自己的分支，并提交在自己的分支上。开发完毕后再合并分支，这样既完成了版本控制，又不影响别人工作

#### 创建与合并分支

本质上分支就是不同的指针

```
#创建分支   -b表示创建并切换
git checkout -b dev

#git branch查看分支
git branch

#

```

笑死，这不就冲突了吗
