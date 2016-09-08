# gitskills
##命令行中新建Github远程仓库,并上传本地代码到远程分支
###curl -u 'username':'password' https://api.github.com/user/repos -d '{"name":"RepoName"}' 
###git remote add origin git@github.com:username/RepoName.git
###git push origin master(your branch name)
##怎么推送本地分支到远程分支上面去？
###git push origin local_branch:remote_branch
###这个操作，local_branch必须为你本地存在的分支，remote_branch为远程分支，如果remote_branch不存在则会自动创建分支。
###类似，git push origin :remote_branch，local_branch留空的话则是删除远程remote_branch分支
