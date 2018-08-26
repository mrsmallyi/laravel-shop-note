 
1. 进入项目共享文件夹code, 配置composer 加速
```
vagrant@homestead:~/code$ composer config -g repo.packagist composer https://packagist.laravel-china.org
```

2. 创建laravel-shop项目
```
vagrant@homestead:~/code$ composer create-project laravel/laravel laravel-shop --prefer-dist "5.5.*"
```
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/bUDcj9jIaQ.png?imageView2/2/w/1240/h/0)
... 中间省略
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/Yw99mURP1x.png?imageView2/2/w/1240/h/0)
到这里，项目laravel-shop创建完成，项目文件情况如下：
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/e2cczUEwGG.png?imageView2/2/w/1240/h/0)

3. 配置 .env 文件 ，设置项目名称: "Laravel Shop" 和 数据库名称: laravel-shop
```
vagrant@homestead:~/code/laravel-shop$ vim .env
```
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/MVCz7hceDX.png?imageView2/2/w/1240/h/0)
**注意：** 项目名称有空格的话，需要双引号括起来，eg: "Laravel Shop"

4. 进入laravl-shop目录，建立Git 代码版本控制
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/4U5ixXChrM.png?imageView2/2/w/1240/h/0)
Laravel 默认的 .gitignore 文件并没有把 public/js 和 public/css 目录排除掉，前端编译后的 JS 和 CSS 文件会被放到这两个目录中，而编译后的文件是不需要加入到版本库的，因此先编辑 .gitignore 文件
5. 将public 文件下css 和 js 文件夹加入到 .gitignore文件里
```
vagrant@homestead:~/code/laravel-shop$ vim .gitignore
```
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/QolVNobzql.png?imageView2/2/w/1240/h/0)
6. 将项目文件提交的git版本仓库
```
vagrant@homestead:~/code/laravel-shop$ git add -A
vagrant@homestead:~/code/laravel-shop$ git commit -m "初始化应用”
```
此时，git commit 出现编码乱码的问题，
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/vs2g4az7Bc.png?imageView2/2/w/1240/h/0)
处理：设置git支持uft8编码
```
$ git config --global core.quotepath false # 显示 status 编码 
$ git config --global gui.encoding utf-8 # 图形界面编码 
$ git config --global i18n.commit.encoding utf-8 # 提交信息编码 
$ git config --global i18n.logoutputencoding utf-8 # 输出 log 编码 
$ export LESSCHARSET=utf-8 
# 最后一条命令是因为 git log 默认使用 less 分页，所以需要 bash 对 less 命令进行 utf-8 编码
```
7. 添加远程版本库分支
```
vagrant@homestead:~/code/laravel-shop$ git remote add origin git:github.com:mrsmallyi/laravel-shop.git
```
![file](https://lccdn.phphub.org/uploads/images/201808/27/26305/iO7eFWtwQt.png?imageView2/2/w/1240/h/0)
8.将commit 代码提交到远程版本库分支
```
vagrant@homestead:~/code/laravel-shop$ git push origin master
```
到这里，项目的创建，配置.env，创建版本库，最后提交代码到github上，算是搭好舞台，后面再跟着教程记录项目的一步步开发过程。