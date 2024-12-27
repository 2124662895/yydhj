----------------------------------
所需软件下载
----------------------------------
termux_0.118.1下载
http://docker.540734621.xyz:57465/s/9BiL
(这是安卓arm64-v8a版本，如果你手机不适配，请自行去如下链接选择合适你手机的版本
https://github.com/termux/termux-app/releases)

MT管理器_2.16.6下载
http://docker.540734621.xyz:57465/s/boC0
----------------------------------
----------------------------------
演示教程:
termux开启drpy-node本地服务器

一、安装
先安装MT管理器、安装termux；
再利用MT管理器并添加本地存储termux。
(以下视频为准：
mt添加本地存储视频.mp4
https://www.alipan.com/s/SbatAyAZMU6)

二、命令
1、更新termux软件包
pkg upgrade

2、安装git
pkg install git

3、克隆道长drpy-node项目
git clone https://github.com/hjdhnx/drpy-node.git
此时可MT管理器查看添加的termux本地存储，发现道长的新项目drpy-node已经克隆下来了

4、安装nodejs
pkg install nodejs

5、进入drpy-node目录
cd drpy-node

6、执行命令
1)、安装所需依赖
npm i  

2)、启动服务
node index.js

等待运行，稍候报错puppeteer，不管他，根据提示:http://localhost:5757或者http://ip:5757即可标识本地drpy-node服务器运行成功。可去壳子添加接口了

如果要停止服务，点击termux里虚拟键盘ctrl+c停止。

8、也可以安装PM2工具来管理进程运行服务
1)、安装PM2
npm install pm2@latest -g

2)、启动服务
进入drpy-node目录,再执行命令

cd drpy-node #已经在当前目录的可忽略此步

pm2 start index.js

此时服务开启，可以壳子调用接口了。

【 pm2 start index.js -f

此时标识无论前面index.js是否开启过运行，都强制开启运行index.js，这种情况下，就会有不止一个index.js进程了，可用pm2 list查看，多余的可停止并删除。】

3)、查看进程
pm2 list

此时可查看进程的id,进程的name,进程数，进程运行状况等

4)、停止、启动与重启进程
pm2 stop 0 #停止
(0就是进程的id，想停止哪个进程就选择他的id)
只是停止进程，但此进程还存在呢，要想启动，就再次命令
pm2 start 0 #启动

运行中的进程可以重启
pm2 restart 0 #重启

5)、删除进程
如果有多个进程，可以delete掉
pm2 delete 0
(0就是进程的id，想删除哪个进程就选择他的id)
delete命令，不管是否运行，都会被强制删除的！
同样的index.js，只保留index的一个进程即可，多余的都删了。

三、接口调用
9、接口
http://localhost:5757/config/1
或者
http://ip:5757/config/1


四、项目更新
10、克隆道长的drpy-node项目后续更新

1). 
启动termux
2). 进入目录
cd drpy-node
3). 更新
git pull

五、puppeteer的安装

色花堂[密+]源播放问题：手机本地就不安装了。

pup(puppeteer)是一款无头浏览器，可以模拟用户手动打开网页，通过一些网站的反爬机制。如需使用，可以通过如下命令安装
npx puppeteer browsers instart chrome

注意：此东西目前只有pc与部分服务器支持安装和使用，手机上海阔不支持，此类源不能使用：比如色花堂[密+]

六、题外话
termux安装后最好安装一次如下软件库
pkg install root-repo #root仓库
pkg install x11-repo #X11仓库

授予Termux访问存储的权限:
termux-setup-storage