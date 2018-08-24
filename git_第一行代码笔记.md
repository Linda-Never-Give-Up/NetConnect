#第一行代码笔记
---
###1 简录
 1.  minifyEnabled指定是否对项目进行混淆，
 2.  proguardFiles用于指定使用的规则文件，
 3.  百分比布局
 4.  include来添加自定义控件
 5.  RecycleView
 6.  Fragment的使用和生命周期
 7.  有关屏幕视频的问题。
 8.  数据库
 9.  运行时权限


###2 git
 01. git config --global user.name "seawaveai" （设置名字、邮箱），（设置单个项目的名字和邮箱呢）
 02. git config --global user.email "aiseawave@gmail.com" (不输入名字、邮箱就可以查看是否配置成功)
 03. git init （初始化）
 04. ls -al （查看文件） /ls -ah
 05. git add .（添加全部）  / git add xxx （添加单个）
 06. git commit -m "First commit,第一次提交代码"  (-m参数来添加描述)
 07. git status （查看文件修改情况）
 08. git diff app/src/main/java/com/example/xikang61/myapplication/MainActivity.java（查看更改内容）
 09. git checkout app/src/main/java/com/example/xikang61/myapplication/MainActivity.java（撤销未提交的修改，这种方式只适合没执行过add命令的文件，如执行过add命令就无法撤销）
 10. git reset HEAD  (先取消添加，然后就可以撤回提交)
 11. git log (查看提交的记录)
 12. 每次提交的id 提交人 提交日期 描述信息。
 13. git log -1 -p （只想查看一条记录加上id 加上 -1，这条记录具体修改了什么加上-p）
 14. git branch version1.0  /git branch (创建分支，查看分支)
 15. git checkout version1.0 （把代码切换到version1.0分支上）
 16. git checkout master
 17. git merge version1.0 （把version1.0版本合并到master上）
 18. git branch -D version1.0 （删除version1.0版本）
 19. git clone www.xxxx.com (远程下载代码)
 20. git push origin master
 21. git pwd 命令用于显示当前目录
 22. ssh-keygen -t rsa -C "youremail@example.com" (创建SSH Key)
 23. git remote add origin git@github.com:seawaveai/coolweather.git
 24. git remote -v
 25. git remote rm origin
 26. 远程库的名称叫github，不叫origin了（名称来标识不同的远程库）
 27. git config --global alias.st status （别名）
 28. --global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用

## git

Git 提供了多种途径，一个方法是先用 git format-patch 命令将本地提交转换为补丁文件或补丁文件序列，再通过邮件发送给核心开发团队。另外一个办法就是搭建一个自己专有的共享版本库，通过邮件创建一个拉拽请求（Pull Request），让核心团队的开发者到自己的版本库来抓取（Pull）


建立主页





















