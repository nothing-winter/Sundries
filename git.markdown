### Git配置
#### **git config [--global/system] <参数(例如下面)>**

    * git config user.name <名字>
    * git config user.email <邮箱>
    * git config --global alias.st status
    * git config --global alias.ci commit
    * git config --global alias.cl clone
    * git config --global alias.pull pull -r

### 初始化仓库
1. git init [仓库名称(创建文件夹的名称)]
2. git clone <远程仓库路径>

### 添加修改文件进暂存区
     * git add <文件名> [文件名2] ...
     * git add .          #添加所有
     * git add -u     #可以添加删除的文件到暂存区
     * git mv welcome.txt README     # 直接移动
     * git add -i          # 选择性提交
### 查看暂存区状态
    git status
        git status -s
    git reset          #仅改变暂存区
        git reset --hard HEAD^     #改变引用，暂存区，工作区
        git reset [--soft | --hard [<提交ID>] 
          参数:- -hard 替换引用，暂存区，工作区
                  --soft 只改变引用
                  --mixed 只改变引用，暂存区

### 提交进本地仓库
     * git commit [--allow-empty] -m “提交说明"
     * git commit --amend -m "提交说明"

### 查看日志 git log
    git log     # 普通内容
    git log --pretty=oneline     #显示一行
    --graph 视图
    -n 显示条数
    -p 显示具体改动
    --stat 仅显示改动文件
    --pretty=raw 显示原始数据，显示提交树
    --pretty=fuller 同时显示作者和提交者
    --pretty=oneline
### 文件恢复
     git checkout -- welcome.txt      #使用暂存区恢复工作去
     git reset HEAD                     #仅暂存区会被恢复
### 清空工作区中未加入到暂存区的文件和目录
     git clean -nd    #查看哪些将会删除
     git clean -fd     #清空
### 远程仓库远程仓库
     git push origin master          #推送本地master分支到远程仓库origin中
     git pull          #拉去远程分支
### 清空工作区中未加入到暂存区的文件和目录
     git clean -nd    #查看哪些将会删除
     git clean -fd     #清空
### 保存工作进度
    git stash          #保存进度
    git stash list     #显示列表
    git stash pop   #恢复进度
### 远程仓库远程仓库
    git push origin master          #推送本地master分支到远程仓库origin中
    git pull          #拉去远程分支
### 里程碑
     git tag                ＃显示里程碑列表
### 版本分支 git branch
    1. 空参数代表显示分支列表
    2. <分支名称> [<commit提交id>] 创建分支，如果填写commit，则以commit创建
    3. -d <branch name> 删除分支
    4. -m <old branch name> <new branch name> 修改分支名称
    * git checkout -b mywork origin 使用origin创建分支mywork
    5. 分支合并git merge <分支ID>
### 忽略文件 .gitignore
##### 使用git rebase
    git rebase --onto C E^ F
    git cherry-pick <commit提交id>

