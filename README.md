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
