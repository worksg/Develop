# 更新Fork的上游分支 

## Clone your fork
    git clone https://github.com/your/develop.git

### 添加上游分支的remote到你的git里面
添加一个叫upstream的remote

    git remote add upstream https://github.com/worksg/develop.git

然后fetch upstream

    git fetch upstream

### 合并上游分支最新的代码到你的主分支中
    git rebase upstream/master
    git merge upstream/master

# Change Repository URL
    git remote set-url origin https://github.com/your/develop-new.git

# Common git command

    git add file1 / git add -A -- file1
    git status
    git stash save -- myStashTag / git stash save -u -- myStashTag
    git stash list
    git stash pop stash@{0} / git stash pop
    git reset HEAD -- file1

    git commit -m "add file1" / git commit -S -m "add file1"
    git log
    git reset HEAD~

    git pull / git fetch origin master && git rebase/merge origin master
    git push / git push origin / git push origin master / git push origin master:master / git push origin HEAD:master # 只用 git push 命令时要设置默认主机 git push --set-upstream origin master

    git push origin :dev / git push origin --delete dev

    git checkout -- file1 # 取消file1在工作区的所有更改
    git checkout -- . # 取消工作区的所有更改
    
# Tag

### Add Tag
    git tag v1.0.0 / git tag -a v1.0.0 / git tag -a v1.0.0 -m '' / git tag -s -a v1.0.0 -m '' / git tag -s -a v1.0.0 -m '' <commit id>
    git push origin v1.0.0

    git push origin --tags # push all tags

### Delete Tag
    git tag -d v1.0.0
    git push origin :v1.0.0

### List Tag
    git tag -l
    git tag -l 'v1.0.*'

### Show Tag
    git show v1.0.0

### checkout Tag
    git checkout v1.0.0

# Squash Pull Request On Github
    https://stackoverflow.com/questions/9994093/automatic-merge-of-pull-requests-on-github-without-the-merge-bubble

    https://help.github.com/articles/checking-out-pull-requests-locally/

# 本地合并远程请求分支

```bash
# github / gitea
git fetch origin pull/ID/head:BRANCHNAME
git checkout BRANCHNAME
```

```bash
# gitlab
git fetch origin merge-requests/ID/head:BRANCHNAME
git checkout BRANCHNAME
```

```bash
# 取回upstream到本地
git fetch upstream
git checkout -b upstreamBranch upstream/master
```

# 创建空白分支
```bash
git checkout --orphan newbranch
git rm -rf .
#... Add some files/folders, then
git commit -am "Initial Commit"
git branch -a
```

# 保护分支说明 

1. it prevents its creation, if not already created, from everybody except users with Maintainer permission
2. it prevents pushes from everybody except users with Maintainer permission
3. it prevents anyone from force pushing to the branch
4. it prevents anyone from deleting the branch

## About force push
```bash
git push <remote> <branch> --force
# Or
git push <remote> <branch> -f
```
> NOTE:
> 
> You only force a push when you need to replace the remote history by your local history.  
> This happens when you rewrite the local history.

> Warning:
> 
> force-pushing will overwrite the remote branch with the state of your local one.
> Warning: be cautious about amending commits that you have already shared with other people.

# Fix windows line encoding in git

- Default Config

        git config --global core.autocrlf true

- 提交时转换为LF，检出时转换为CRLF

        git config --global core.autocrlf true

- 提交时转换为LF，检出时不转换

        git config --global core.autocrlf input

- 提交检出均不转换

        git config --global core.autocrlf false

### 多个系统平台上工作，推荐将 git 做如下配置
```bash
git config --global core.autocrlf input
git config --global core.safecrlf warn
```

### 忽略文件权限值修改
```bash
git config --global core.fileMode false
```

### vs-code config
    "files.eol": "\n"

# .gitignore
    # 这是注释行，将被忽略
    *.a       # 忽略所有以.a为扩展名的文件
    !lib.a    # 但是名为lib.a的文件或目录不要忽略，即使前面设置了对*.a的忽略
    /TODO     # 只忽略此目录下的TODO文件，子目录中的TODO文件不忽略
    build/    # 忽略所有build目录下的文件，但如果是名为build的文件则不忽略
    doc/*.txt # ignore doc/notes.txt, but not doc/server/arch.txt
    doc/**/*.pdf # ignore all .pdf files in the doc/ directory

    /fd1/* # 忽略根目录下的 /fd1/ 目录的全部内容
    fd1/* # 忽略目录fd1下的全部内容，包括子目录中的fd1目录

# git proxy && go get proxy

### Windows(CMD)
    set http_proxy=http://localhost:1080
    set https_proxy=http://localhost:1080

### Linux / Windows(MINGW64)
    export http_proxy=http://localhost:1080
    export https_proxy=http://localhost:1080

### Global Git Proxy
    git config --global http.proxy http://127.0.0.1:10809
    git config --global https.proxy http://127.0.0.1:10809
    # OR
    git config --global http.proxy socks5://<host>:<port> / socks5h://<host>:<port>
    git config --global https.proxy socks5://<host>:<port> / socks5h://<host>:<port>
    
    # Disable proxy
    git config --global --unset http.proxy
    git config --global --unset https.proxy
