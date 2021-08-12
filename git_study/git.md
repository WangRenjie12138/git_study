## 安装

### 配置信息

```bash
$git config --global user.name "Wang Renjie"
$git config --global user.email "857638220@qq.com"
```

### 创建版本库

```bash
$git init    # init git, transfer the folder to git resposity

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
# if we rollback and want to rollback again, we can use *git feflog* to get all my command history
$git reflog
```



#### 工作区和暂存区







