# Git - 常用命令

```text
git init here # 创建本地仓库(repository)，将会在文件夹下创建一个 .git 文件夹，.git 文件夹里存储了所有的版本信息、标记等内容
git remote add origin git@github.com:用户名/仓库名.git # 把本地仓库和远程仓库关联起来。如果不执行这个命令的话，每次 push 的时候都需要指定远程服务器的地址
git add # 从本地仓库增删，结果将会保存到本机的缓存里面
git rm
git commit -m "comments" # 提交，把本机缓存中的内容提交到本机的 HEAD 里面
git push origin master # 把本地的 commit(提交) push 到远程服务器上
git pull origin master # 从远程服务器 pull 新的改动
git status # 查看状态
git add -A # 提交全部修改
```

> git 配置:
>
> ```text
> git config --global user.name "xxx" # 配置用户名，上传本地 repository 到服务器上的时候，在 Github 上会显示这里配置的上传者信息
> git config --global user.email "xxx" # 配置邮箱
> git config --list # 查看配置列表
> ```
>
> 配置 sshkey: 参考[Mac 配置 ssh](mac-pei-zhi-ssh.md)
>
> 建立仓库 repository:
>
> ```text
> git init here # 创建本地仓库
> git remote add origin git@github.com:用户名/仓库名.git # 把本地仓库和远程仓库关联起来， 如果不执行这个命令的话，每次 push 的时候都需要指定远程服务器的地址
> ```
>
> 从远程仓库中下载新的改动:
>
> ```text
> git pull origin master
> ```
>
> 提交本地修改到远程仓库中:
>
> ```text
> git add
> git add -A # 将改动添加到本地仓库中
> git rm xxx # 从本地仓库中删除指定文件
> git rm -r xxx # 从本地仓库中删除指定文件夹
> git commit -m "注释" # 把本机缓存中的内容提交到本机的 HEAD 里面
> git push origin master # 把本地的 commit push 到远程仓库中
> ```
>
> 编辑提交
>
> ```text
> git rebase -i HEAD~2 # 编辑最近两次提交
>     # p, pick = use commit
>     # r, reword = use commit, but edit the commit message
>     # e, edit = use commit, but stop for amending
>     # s, squash = use commit, but meld into previous commit
>     # f, fixup = like "squash", but discard this commit's log message
>     # x, exec = run command (the rest of the line) using shell
>     # d, drop = remove commit
> git reset HEAD~2 # 回退最近两次提交(commit 会丢失, 两次修改的代码会整合在一起)
> ```

