# Mac 配置 ssh

## 配置单个公钥

> 检查是否存在 ~/.ssh 文件夹，如果不存在则先新建，然后使用 ssh-keygen 生成文件

```text
# 没有.ssh文件夹，才需要创建
mkdir ~/.ssh

cd ~/.ssh

# -t 指定密钥类型，默认即 rsa ，可以省略
# -C 设置注释文字，比如你的邮箱（注意是大写的C，并且邮箱左右有引号）
# 此方法会默认在`~/.ssh/`下生成一个名字`id_rsa`的私钥文件，及`id_rsa.pub`的公钥文件
ssh-keygen -t rsa -C "{your_email@email.com}"
```

## 配置多个公钥

```text
# 以下两种任选一种即可
# 1. 生成新的ssh key并命名为`custom_rsa`
ssh-keygen -t rsa -C "your_email@email.com" -f ~/.ssh/custom_rsa

# 2. 或 打以下命令后，在询问时输入名称
ssh-keygen -t rsa -C "your_email@email.com"
```

> 一路回车，然后复制新生成的 custom\_rsa.pub 里面的内容，后面需要把内容粘贴到服务器上。

```text
# 复制id_rsa.pub里的内容到剪贴板，或是手动去 ~/.ssh/custom_rsa.pub 复制
pbcopy < ~/.ssh/custom_rsa.pub
```

> 修改 ~/.ssh 下的 config 文件，

```text
vim ~/.ssh/config
```

> 实例：

```text
# desc: github (github@email.com)
Host github.com
    Hostname github.com
    User git
    PreferredAuthentications publickey
    Identityfile ~/.ssh/github

# desc: my_server_user (your_email@email.com)
Host your_domain_name_or_ip
    HostName your_domain_name_or_ip
    User git
    IdentityFile ~/.ssh/custom_rsa

# 以上各字段说明：
# Host：主机名字，不能重名
# HostName：主机所在域名或IP
# User：服务器上的用户名
# PreferredAuthentications：不填此行的话，如果pubkey验证不通过可以用密码方式；填了`publickey`只能通过公钥验证的方式
# IdentityFile：私钥路径
```

要让两个 `ssh` 不互相影响，并且 git 操作时能智能匹配私钥, 上面的 `Host` 字段其实是任意的，`git` 操作时会有一个映射，将 `Host` 映射到目标域名或 `ip (HostName)` 我们可以这么配置:

```text
Host a.github.com
Hostname github.com
User git
Identityfile ~/.ssh/a_github_rsa

Host b.github.com
HostName github.com
User git  // 用户名称
IdentityFile ~/.ssh/b_github_rsa
```

> ***注意：公私钥命名要对应***

> ssh 的地址更改, 如 `A` 账号的 `repo` 仓库原本的地址是`git@github.com:A/repo.git`，配置了 `ssh` 后，便可以使用`git@a.github.com:A/repo.git`

> 运行 `ssh -T a.github.com` 测试

