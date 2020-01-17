# Git 使用指南

## 创建RSA

使用`ssh-keygen -t rsa -C "你的email地址"`创建，注意生成的.pub文件是公钥。

## 初始化仓库

`git init`会将本地文件夹创建为Git仓库。

## 查看状态

`git status`

## 添加文件

`git add`

`git add .`将会添加所有更改

注意这里添加的更改，而不是文件。所以当我们在添加新的文件之后再对其修改就会产生新的添加请求（如果当前文件被追踪）

## 查看差异

查看当前有哪些东西被修改了

`git diff`

## 恢复修改

`git reset`

## 设置用户信息

`git config --clobal user.name "User Name"`

`git config --globel user.email "adderss@dimain.com"`

## 提交更改

`git commit` 就打开文本编辑器说明更改

一条命令提交更改：`-m "Commits"`

不用add直接提交 `-a Commits`

设置打开其他编辑器`git config global core.editor vim`

## 忽略文件

新建`.gitignore` 忽略名单

直接输入文件名称就可以了！

## 停止追踪文件更改

`git rm --catched FileName`

此操作不会真的删除文件，而是在git内部删除这个文件了！


## Git 分支

查看分支 `git branch`

### 创建分支

`git branch BranchName`

### 切换分支

`git checkout BranchName`

### 合并分支

`git merge SubBranchName`

解决冲突？

### 删除分支

`git baranch -d BranchName`

使用D强制删除

## 提交到Github

### 绑定远程地址

`git remote add origin https://github.com/xxx/xxx.git`

### 提交！

`git push --set-upstream origin master`

### 设置保存密码

`git config credential.helper store`

这样下一次就不会提示输入账户信息了。

# 克隆仓库

`git clone https://github.com/xxx/xxx`

# 取得最新修改

`git pull`
