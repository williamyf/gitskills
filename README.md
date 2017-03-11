# gitskills
##如何创建SSH Key？
###在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：$ ssh-keygen -t rsa -C "youremail@example.com"
###你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。
###如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
##命令行中新建Github远程仓库,并上传本地代码到远程分支
###curl -u 'username':'password' https://api.github.com/user/repos -d '{"name":"RepoName"}' 
###git remote add origin git@github.com:username/RepoName.git
###git push -u origin master(master is your branch name)
###加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令(简化为 git push origin master)。
##怎么推送本地分支到远程分支上面去？
###git push origin local_branch:remote_branch
###这个操作，local_branch必须为你本地存在的分支，remote_branch为远程分支，如果remote_branch不存在则会自动创建分支。
###类似，git push origin :remote_branch，local_branch留空的话则是删除远程remote_branch分支
##
##解决ssh-connect-to-host-github-com-port-22-connection-timed-out
###解决办法：（linux下）
~$ cd ~
~$ cd .ssh/
~$ touch config
在.ssh目录下创建一个config文件，输入如下内容：
'''
Host github.com 
User xxx@163.com （你注册github时的邮箱，这里使用注册的用户名也行） 
Hostname ssh.github.com 
PreferredAuthentications publickey 
IdentityFile ~/.ssh/id_rsa 
Port 443
'''
可以把以上内容拷到config文件里面，注意修改你的邮箱，保存并关闭 
进行测试是否连接上github.com 
~$ ssh -T git@github.com 
The authenticity of host ‘[ssh.github.com]:443 ([207.97.227.248]:443)’ can’t be established. 
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48. 
Are you sure you want to continue connecting (yes/no)? y 
Please type ‘yes’ or ‘no’: yes 
Warning: Permanently added ‘[ssh.github.com]:443,[207.97.227.248]:443’ (RSA) to the list of known hosts. 
Hi zhou411424! You’ve successfully authenticated, but GitHub does not provide shell access. 
出现Hi xxx!……表示连接成功。
##
##git无法pull仓库refusing to merge unrelated histories
###git pull origin master --allow-unrelated-histories
