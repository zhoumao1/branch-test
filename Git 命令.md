[toc]

# Git 命令

## 安装&设置

### 出现权限被拒绝

```shell
git@github.com: Permission denied (publickey).
      Could not read from remote repository.

      Please make sure you have the correct access rights
      and the repository exists.
```

输入以下命令

1. 进入`.ssh`目录

   ```shell
   cd ~/.ssh
   ```

2. 生成 SSH 公钥，并输入 GitHub 密码

   ```shell
   ssh-keygen -t rsa -C "244****181@qq.com"
   ```

3. 添加 SSH 公钥到 GitHub， 把`id_rsa.pub`内容复制到`key`里面 

4. 测试是否生效

   ```shell
   ssh -T git@github.com
   ```

   如果看到这些内容，直接确定即可

   ```shell
   The authenticity of host 'github.com (207.97.227.239)' can't be established. 
   RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48. 
   Are you sure you want to continue connecting (yes/no)?
   
   Hi {username}! 
   You've successfully authenticated, but GitHub does not provide shell access.
   ```

### 基于远程跟踪分支创建本地分支


如果你想基于远程跟踪分支创建本地分支（在本地分支上工作）,你可以使用如下命令：`git branch –track`或`git checkout –track -b`，两个命令都可以让你切换到新创建的本地分支。例如你用`git branch -r命令`看到一个远程跟踪分支的名称为`origin/refactored` 是你所需要的，你可以使用下面的命令： 

## 提交

1. 提交工作区所有文件到暂存区：`git add .`
2. 提交工作区中指定文件到暂存区：`git add   ...`;
3. 提交工作区中某个文件夹中所有文件到暂存区：`git add [dir]`;

## 暂存区上的操作命令

### 提交文件到版本库 

1. 将暂存区中的文件提交到本地仓库中，即打上新版本：`git commit -m "commit_info"`;
2. 将所有已经使用git管理过的文件暂存后一并提交，跳过add到暂存区的过程：`git commit -a -m "commit_info"`;

### 分支管理

1. 显示所有分支（本地仓库）：`git branch`
2. **创建分支**：`git branch <branch_name>`，例如`git branch slide`
3. 从当前分支**切换**到其他分支：`git checkout <branch_name>`
4. **新建并切换**到新建的分支上：`git checkout -b <branch_name>`
5. **删除分支**：`git branch -d <branch_name>`
6. 将当前分支与指定分支进行**合并**：`git merge <branch_name>`
7. 把远程分支合并到当前分支：`git merge <remote_name>/<branch_name>`，如：`git merge origin/master`如果是单线的历史分支不存在任何需要解决的分歧，只是简单的将HEAD指针前移，所以这种合并过程可以称为快进（Fast forward），而如果是历史分支是分叉的，会以当前分叉的两个分支作为两个祖先，创建新的提交对象；如果在合并分支时，遇到合并冲突需要人工解决后，再才能提交；

### 本地仓库上的操作

1. 查看本地仓库关联的远程仓库：`git remote`，若显示地址：`git remote -v`

2. 添加远程仓库并取别名：`git remote add <别名> <url>`

3. 从远程仓库中抓取本地仓库中没有的更新：`git fetch <remote_name>`，使用`fetch`只是将远程分支内容拉取到本地仓库，并不会自动合并带当前分支，只能人工合并

4. 将本地仓库的某分支推送到远程分支上：`git push <remote_name> <branch_name>`，如`git push origin master`。

   如果想将本地分支推送到远程仓库的不同名分支：`git push <remote_name> <local_branch>:<remote_branch>`，如`git push origin slide:master`将本地分支推送到远程的主分支

> 转载: [git基本操作，一篇就够了](https://juejin.im/post/5ae072906fb9a07a9e4ce596)

是是是