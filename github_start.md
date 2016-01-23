在国内这种“严密”环境下相信大家都会遇到访问某个国外网站慢的问题，作为程序猿，经常也会被朋友找来解决该问题，当然，对于像github这种程序猿必须访问的网站，如何快速访问对于我们平时的开发和学习是非常有帮助的。今天小便就给大家带来了福利，一步一步教大家装逼一把。当然在某些网段，可能你不需要设置，但是在某些大公司或者涉密单位，像github这类网站是被限制的。

      下面我以os系统为例，windows类似，大家可以自行尝试。

      首先，打开Launchpad 也就是桌面上的小火箭图标，找到终端有些系统可能会显示 terminal。进入终端命令行模式，输入sudo vi /etc/hosts，有的文章误导人，说是使用su，其实默认情况下，OS X是不支持su命令的，应该使用sudo。sudo是允许用户以超级用户的权限执行操作的一个命令，如果要启用su命令，操作如下： sudo passwd root。

      然后打开hosts文件后，进入编辑模式，不熟悉vi命令的建议在网上学习下，输入i进入编辑命令。此时，我们需要加入github的host地址，接下来我们需要知道github.com和github.global.ssl.fastly.net域名对应的ip地址。

      用浏览器访问 IPAddress.com 使用 IP Lookup 工具获得这个域名的ip地址，该网站可能需要梯子，输入上述域名后，分别获得github.com和github.global.ssl.fastly.net对应的ip，比如192.168.xx.xx和185.31.17.xx。准备工作做完之后，在vi打开的hosts文件中添加如下格式：

192.168.xx.xx github.com
185.31.17.xx github.global.ssl.fastly.net
      然后esc退出编辑模式，输入wq，保存hosts文件，修改hosts结束。此时，如果直接访问github可能不会立即生效，因为有DNS缓存，并没有按照最新的修改配置访问。

      最后，我们在命令行中输入sudo dscacheutil -flushcache，更新DNS缓存。此时，重新访问github，奇迹诞生了，访问速度嗖嗖的，完美解决访问慢的问题。妈妈再也不用 担心猿的继续深造了，大家可以试试，为人民服务。如果大家感兴趣可以看看我写的其他文章，本人全部原创，拒绝抄袭。
      
# Github start
192.30.252.141	gist.github.com
192.30.252.131  github.com
23.235.44.249   github.global.ssl.fastly.net
# Github end