linux命令
ls 展示当前工作目录
    -a 全部内容
    -l 列表的样式显示
    -h 显示文件大小

cd 切换工作目录 
    cd 没有选项
    cd 直接执行回到HOME目录
    cd ~切换HOME目录
    cd .切换当前目录
    cd ..切换上一级目录

pwd 查看当前工作目录

mkdir 创建新的目录（文件夹）
    -p 创建多级目录

touch 创建文件

cat 参看文件内容

more 查看文件内容以翻页的形式查看内容空格翻页，q退出

cp 用于复制文件或文件夹
    -r 用于复制文件夹使用，表示递归
    语法：cp [-r] 参数1 参数2
    参数1：被复制的文件或文件夹
    参数2: 要复制去的地方

mv 用于移动文件或文件夹
    语法：参数1 参数2 
    参数1：被移动的文件或文件夹
    参数2：要移动的地方，如果目标不存在即对其**改名***

rm 删除文件或文件夹
    rm -r 文件夹删除（可选）
    rm -f 强制删除 （不提示《一般用于root用户）（可选）
    语法：rm -rf 参数1 。。。 参数n
    参数：表示被删除的文件或文件夹路径，支持多个，空格隔开，支持通配符*
    
which 查找命令的程序文件
    语法：which 要查找的命令
    示例：which pwd
    
find 用于查找指点文件
    find -name 按文件名查找
        语法：find 起始路径 -name 被查找的文件名
        示例：find \ -name test.txt
    find -size 按文件大小查找
        语法：find 起始路径 -size +｜-[kmg]
        示例：find \ -size +1g
        示例解释：从根目录开始查找大于1g的文件，-1g则小雨kmg则是单位

grep 从文件中通过关键字过滤文件行
    grep -n 表示结果中显示匹配的行的行号（可选）
    语法：grep 参数1:关键字 参数1:文件路径
    参数1:关键字必填，表示过滤的关键字
    参数2:文件路径，必填，表示要过滤内容的文件路径  

wc 统计文件的行数、单词数量、字节数、字符数、
    wc -c 字节数
    wc -m 字符数
    wc -l 行数
    wc -w 单词数
    不带参数默认统计：行数、单词数、字节数
    语法：wc 参数：文件路径
    
|   将管道符左边命令的结果，作为右边命令的输入

echo 在命令行输出指点内容
    语法：echo 参数：输出的内容

``  反引号符，被``包围的内容，会被作为命令执行，而非普通字符

tail 查看文件尾部内容，并可以持续跟踪
    语法：tail 选项：-f -[num] 参数：文件路径
    -f 表示持续跟踪
    -num 表示查看尾部多少行不填默认10行
    示例：tail -f -5 test.txt
    示例解释：持续跟踪test文件最后5行内容
    
>   将左侧命令的结果，覆盖写入到右侧指定的文件中
>>  将左侧命令的结果，覆盖写入到右侧指定的文件中

vi/vim编辑器
    vi/vim 参数：文件路径 

linux系统的超级管理用户是：root用户
    exit退出root用户
su 切换用户名
    语法：su 选项：- 参数：用户名
    选项：- 表示切换后加载环境变量
    参数：用户名可以省略，默认切换root用户

sudo 可以让一条普通命令带有root权限
    语法：sudo 其他命令
    需要以root用户执行visudo命令，增加配置方可让普通普通用户右sudo命令的执行权限

linux 用户管理模式
    linux 可以支持多用户，多用户组，用户加入多个组
    linux 权限管控的单元是用户级别和用户组级别

groupadd 添加组
groupdel 删除组
useradd 添加用户
userdel 删除用户
usermod 修改用户组
id 查看用户信息
getent passwd 查看系统全部用户信息
getent group 查看系统全部组信息

文件权限控制信息
由10位组成
第一位可是-，r，l
-表示该文件是文件
r表示该文件是文件夹
l表示该文件是软链接

第二位到第四位是所属用户权限
rwx
第五位到第七位是所属用户组权限
rwx
第八位到第十位是其他用户权限
rwx
-----
r表示可读
w表示增删改
x表示执行，如cd进入文件夹

chmod 修改文件、文件夹的权限信息**只有所属用户或root用户可以修改**
    语法：chomod 选项：-R 参数1:权限 参数2：文件夹
    选项：-R，对文件夹内的全部内容应用同样的操作
    示例：chmod u=wrx,g=rx,o=x test.txt
    示例解释：u表示user所属用户权限，g表示group组权限，o表示other其他用户权限

权限的数字序号 
    r代表4，w代表2，x代表1

chown 修改文件、文件夹的所属用户，用户组**只可root用户执行**
    语法：chown 选项：-R 参数：用户：用户组 文件或文件夹
    选项：-R 对文件夹内的全部内容应用同样的操作
    参数：用户修改所属用户
    参数：：用于分隔用户和用户组
    参数：用户组修改所属用户组

ctrl+c 强制停止
ctrl+d 退出登出
history 查看历史命令
！命令前缀，自动匹配上一个命令
ctrl+r 搜索历史命令
ctrl+a｜e 光标移动到命令开始或结束
ctel+<|> 左右跳单词
ctrl+l 清理屏幕
clear 清理屏幕

centos 使用yum命令联网管理软件安装
    语法：yum 选项：-y install remove search 软件名称
ubuntu系统中使用apt命令联网管理软件安装
    语法：apt 选项：-y install remove search 软件名称
    选项：-y自动确认

systemctl 可以控制软件服务的启动、关闭、开机自启
    系统内置服务均可被systemctl控制
    第三方软件如果自动注册了可以被systemctl控制
    语法：systemctl start ｜stop ｜status ｜enable ｜disable 参数：服务名
    restart 重启服务
    start 开启服务
    stop 停止服务
    status 服务的状态
    enable 开机自启
    disable 开机关闭

软链接 可以将文件、文件夹链接到其他位置，链接只是一个指向，并不是物理移动，类似windoes的快捷方式

软链接的使用语法 ln 选项：-s 参数1 参数2
    选项：-s 创建软链接
    参数1:被链接的文件或文件夹
    参数2:被链接的目的地

date 可以查看日期时间，并可以格式化显示形式以及做日期计算
    语法：date -d +格式化字符串

ifconfig 查看本机的ip地址
hostname 查看主机名
    hostname set-hostname 主机名，修改主机名，**root权限**

ping 可以测试到某服务器是否可联通
    ping 选项：-c num 参数：ip或主机名
    选项：-c 3 测试的次数
    默认无限次数
wget 可以进行网络文件下载
    wget 选项：-b 参数：url 
    选项：-b 后台下载，会将日志写入当前工作目录的wget-log文件

curl 可以发起网络请求
    curl 选项：-o 参数：url
    选项：-o 用于下载使用

端口

进程是指程序在操作系统运行后被注册为系统内的一个进程，并拥有独立的id

ps -ef 查看进程信息
ps -ef | grep关键字过滤指定关键词进程信息
kill -9 进程号 关闭指定进程号的进程，-9强制删除

top 查看cpu、内存使用情况，类似windows的任务管理器

df 查看硬盘的使用情况
df -h 以更加人性化的单位显示，磁盘使用率
iostat -x 查看cpu、磁盘的相关信息，磁盘速率
sar -n DEV 查看网络的相关统计
env 查看当前系统配置的环境变量信息
$符号 取出环境变量的值
source 立刻生效

安装lrzsz
rz 文件上传
sz 文件下载

tar 选项：-z -x -c -f -c 参数：文件路径
    -c 创建解压文件
    -v 查看解压\压缩过程
    -x 解压模式
    -f 指定解压压缩的文件
    -z gzip模式
    -C 指定解压的路径
    -z建议在选项组的开头，-f在选项组的尾部，-C单独使用

zip 压缩文件
    -r 压缩文件夹使用
unzip -d 参数 解压文件
    -d 指定解压去的目录