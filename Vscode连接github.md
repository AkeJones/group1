# Vscode连接github

1.[vscode如何链接github](http://t.csdnimg.cn/pFf3A)

误以为要在vscode重新生成密钥，实际只要加ssh -T git@github.com

vscode新建终端

```
PS D:\git>ssh -T git@github.com
failed to connect to github.com port 443 after 21116 ms: Couldn't connect to server
```

2.[Failed to connect to github.com port 443 after 21111 ms: Couldn‘t connect to server](http://t.csdnimg.cn/ppTBC)

没用。其中电脑设置的防火墙对象是程序，没有网站

改成用ssh地址，报错ssh: connect to host github.com port 22: Connection timed out

3.[“ssh:connect to host github.com port 22: Connection timed out“问题的解决](http://t.csdnimg.cn/a4YEk)

评论区代码修改为ssh -T git@ssh.github.com 

解决。

4.[vscode如何链接github](http://t.csdnimg.cn/pFf3A)

继续，直到

点击Changes里面，vscode中更改了的文件右侧的“+”，将其放入Staged Changes中，然后点击Commit即可上传到github repository中。


```
HP@LAPTOP-D7931K0R MINGW64 ~
$ ssh -T git@ssh.github.com
The authenticity of host 'ssh.github.com (20.205.243.160)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'ssh.github.com' (ED25519) to the list of known hosts.
Hi AkeJones! You've successfully authenticated, but GitHub does not provide shell access.

HP@LAPTOP-D7931K0R MINGW64 ~
$ git remote add origin https://github.com/AkeJones/group1.git
fatal: not a git repository (or any of the parent directories): .git
 
HP@LAPTOP-D7931K0R MINGW64 ~
$ git init
Initialized empty Git repository in C:/Users/HP/.git/

HP@LAPTOP-D7931K0R MINGW64 ~ (master)
$ git remote add origin https://github.com/AkeJones/group1.git

HP@LAPTOP-D7931K0R MINGW64 ~ (master)
$ git remote add origin https://github.com/AkeJones/group1.git
error: remote origin already exists.
```

5.[vscode使用git连接github](http://t.csdnimg.cn/fUBJK)

三四五步。

第四步推送时报错，显示命令输出：

》 git push -u group1 main#》应为>
fatal: unable to access 'https://github.com/AkeJones/group1.git/': Failed to connect to github.com port 443 after 21120 ms: Couldn't connect to server

6.[Failed to connect to github.com port 443 after 21129 ms: Couldn‘t connect to server](http://t.csdnimg.cn/rQYxX)

没用。

没试第一种取消代理的方式。

第二种拉取，弹窗分支"main"没有远程分支，是否要创建分支？确定之后也 Couldn‘t connect to server

7.[clone报错fatal: unable to access ‘https://[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020).com/…’: Failed to connect to github.com port 443 after 21096 ms: Couldn’t connect to server](https://blog.csdn.net/weixin_46191137/article/details/133739981?ops_request_misc=%7B%22request%5Fid%22%3A%22170609539116800182110114%22%2C%22scm%22%3A%2220140713.130102334.pc%5Fall.%22%7D&request_id=170609539116800182110114&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-133739981-null-null.142^v99^pc_search_result_base3&utm_term=fatal%3A unable to access https%3A%2F%2Fgithub.com%2FAkeJones%2Fgroup1.git%2F%3A Failed to connect to github.com port 443 after 21120 ms%3A Couldnt connect to server&spm=1018.2226.3001.4187)

Git Credential Manager by [Git Ecosystem](https://github.com/git-ecosystem)请求github授权

弹窗：Can't push refs to remote. Try running "Pull" first to integrate your changes.

显示命令输出：failed to push some refs to 'https://github.com/AkeJones/group1.git'

回到6，先pull再push

》git pull --tags
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

git branch --set-upstream-to=group1/<branch> main

8.按终端提示

PS D:\git> git branch --set-upstream-to=group1/<branch> main

fatal: the requested upstream branch 'group1/<branch>' does not exist
hint: 
hint: If you are planning on basing your work on an upstream
hint: branch that already exists at the remote, you may need to
hint: run "git fetch" to retrieve it.
hint: 
hint: If you are planning to push out a new local branch that
hint: will track its remote counterpart, you may want to use
hint: "git push -u" to set the upstream config as you push.
hint: Disable this message with "git config advice.setUpstreamFailure false"

PS D:\git> git fetch  

PS D:\git> git pull group1 main
From https://github.com/AkeJones/group1

*branch            main       -> FETCH_HEAD
fatal: refusing to merge unrelated histories

9.[git提交 出现 ： fatal: refusing to merge unrelated histories](https://blog.csdn.net/Lovely_red_scarf/article/details/125779380?ops_request_misc=%7B%22request%5Fid%22%3A%22170609765416800222839230%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=170609765416800222839230&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-2-125779380-null-null.142^v99^pc_search_result_base3&utm_term=fatal%3A refusing to merge unrelated histories&spm=1018.2226.3001.4187)

第一种方案
