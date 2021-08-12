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

```
delete file in 
```

https://www.liaoxuefeng.com/wiki/896043488029600/900002180232448
