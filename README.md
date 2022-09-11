# rebatedog
返利狗发单软件 返利狗返利结算管理软件
1,Windows下的安装：
将下载下来的压缩包解压到一处，运行里面的狗头主程序即可。
双击RebateDog.Server.exe运行
默认端口号是15888
想修改端口号，到目录下的Appsetting.json内修改
访问机器IP+默认端口号15888即可访问管理。


2，Linux的安装
我习惯用WinSCP这个文件管理工具。
上传到一个用户目录。建议创建一个新的目录。
将压缩包解压。
用ssh工具连接到linux主机，并进入返利狗所在目录。
后台运行返利狗
./start.sh
后台停止运行
./stop.sh
调试运行
./RebateDog.Server --urls="http://*:15888"
运行起来，访问机器IP+默认端口号15888即可访问管理。
如图：


3，Docker版本的安装方法
在DockerHub中的名字：zhaoyangguang/rebatedog
1，先拉镜像
docker pull zhaoyangguang/rebatedog:latest
2，创建容器并运行，注意下面的$PWD/data是你的本机目录，将主机当前目录下的data目录挂载到容器的/app/data目录
docker run -dit \
  -v $PWD/data:/app/data  \
  -p 15888:15888 \
  --name rebatedog \
  --hostname rebatedog \
  --restart unless-stopped \
  zhaoyangguang/rebatedog:latest
3，再次提醒：生产用请一定要映射数据库目录出来，否则你每次都得配置，客户数据也会丢失。 Docker内的数据库目录是/app/data
3,打开浏览器访问容器IP+上面端口15888访问即可！

注意：所有平台返利狗的配置文件数据文件都在运行目录下的
/data
文件夹里面，请保存备份好你的数据，丢失概不负责！

其他使用文档请访问https://www.yuque.com/sunnysoft/
