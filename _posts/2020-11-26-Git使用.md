
# GIT 使用

工作区 - 暂存区 - 本地仓库

1. 在电脑上创建一个文件夹作为工作区
2. 打开文件夹右键 git base here 进入当前目录
3. 工作区持有项目的实际文件
4. 暂存区和本地仓库，不需要我们操作

## readme 文档
1. readme文件可以是txt文档，也可以是md文档
2. 一般和项目放在一起，作为项目的说明文档

## 全局配置
1. 配置用户名： git  config --global user.name "github用户名"
2. 配置用户邮箱： git config --global user.email "github验证邮箱"
3. 一台电脑配置一次就行
4. 查看配置信息 git config --list

## 初始化
1. 命令 git init 初始化版本库
2. 单钱目录路劲有（master）代表初始化成功
3. 在当前目录下会生成一个隐藏文件 .git 代表这是一个版本库
4. 千万别操作 .git文件

## 工作区内容提交到本地仓库
1. 执行命令 git add 文件名 将工作区的内容提交到暂存区
2. 命令 git add . 将所有变动（新增、修改、删除）提交到暂存区
3. 从暂存区提交到本地仓库 git commit -m "提交注释"

## 版本回退
1. git reset --hard HEAD^ 回退到上一个版本（一个^表示上一个版本）
2. git reset --hard 版本号的哈希值   回退到指定的版本

## 辅助命令
1. 命令 git status 查看当前目录下的操作状态
2.  git log 查看日志
3. git reflog 查看简版日志

## 将本地仓库提交到远程仓库
1. 在github创建一个远程仓库 git2010
2. 本地工作区先提交到本地仓库
3. git remote add origin 远程仓库地址 本地仓库和远程仓库关联
4. git remote -v 查看本地仓库关联的远程仓库
5. 先更新pull 在 push  避免代码合并
6. git push -u origin master 第一次执行
    git push 把本地仓库推送到远程仓库
    -u origin master 设置默认提交master分支到origin
7. git push -u -f origin master 强制推送到远程，不推荐！！

## 下载项目到本地
1. 克隆项目：git clone 项目远程仓库地址 整个版本库克隆下来
2. git clone 适用于本地没有项目，直接从远程下载到本地
3. 一定要先把工作区的修改提交到本地仓库，再更新远程到本地
4. 如果本地有该项目，应该直接更新到本地：git pull
5. git fetch 将远程更新到本地 

## 分支操作
1. 查看当前仓库的所有分支：git branch
2. 当前分支前面带有星号 *
3. 查看远程分支：git branch -r
4. 创建分支：git branch 分支名
5. 切换分支：git checkout 分支名 切换分支之后，工作区的代码切换到对应分支的代码
6. 合并分支: git merge 分支名 把“分支名”合并到当前分支
7. 删除分支：git branch -d 分支名
8. git pull origin dev 更新代码到本地，自动合并到当前分支
9. git fetch origin dev 更新代码到本地，不会合并到当前分支
10. git merge FETCH_HEAD 把FETCH_HEAD合并到当前的分支


## 添加协作者
1. 在当前项目位置 点击 settings
2. 选择 Manage access
3. 点击Invite a collaborator 添加协作者
4. 受邀人收到邮件后点击接收邀请

# 配合ssh密匙
1. 生成密匙：ssh-keygen -t rsa -C '邮箱地址'
2. 找到.ssh/id_rsa.pub 文件
3. 复制里面的内容
4. github 个人头像 -> settings
5. 选择 SSH keys
6. new SSH key
7. 粘贴复制id_rsa.pub 文件的内容
8. 点击add SSH key
9. 把本地仓库和远程仓库关联（使用ssh地址）
10. 重新配置远程地址（origin）
11. 删除原来的配置：git remote rm origin
12. 添加新的关联：git remote add origin ssh地址


## git忽略列表
1. 创建文件 .gitignore
2. 忽略文件列表
3. 在忽略列表中,列出不需要提交到版本库的文件及目录