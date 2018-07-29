# 使用说明：
本程序提供一键下载中国大学MOOC视频、课件功能，仅供学习使用。
以下为程序流程：
1. 账号密码
2. 下载路径（程序会将课件下载到该文件夹）
3. 课程号（在需要学习的MOOC课程网址中找到'XXX-ddddddd'格式中后面的数字部分 将其复制过来即可，其中XXX指大写字母，为学校名英文缩写，其后为一串数字，就是课程号）
4. 学期号（选择下载第几次开课内容）
5. 周次（按照章节次序选择课程，与课程名中的周次无关，支持单个数字、数字-数字的输入，其中单个整数0和all为下载全部）
6. 课件类型（1对应视频、3对应文档、4对应附件、all对应所有都下，支持多个数字组合）
7. 视频清晰度（选择下视频时会询问，sd对应标清、hd对应高清、shd对应超高清，请根据自己流量情况进行选择）
8. 等待几秒开始下载，下载提示增加信息提示头，错误[Error]，成功[Success]，下载[Loading]，信息[Info]


# 注意事项：
1. 当前输入容错功能较低，请尽量按照输入提示进行输入
2. 如果有下载完成的提示信息仅代表已将所有下载任务尝试下载过一遍，并不代表每个都下载成功，请仔细观察是否有下载失败的提示，并根据提示进行操作
3. 进程数看需求选择，内置限制3-10
4. 可通过任务管理器查看下载情况，如果程序对应硬盘无活动，请用鼠标点击程序后按回车便可重新唤醒程序
5. 请不要在主进程运行时候修改config.txt（打开也不行）
6. Playlistの食用方法：将该文件直接拖到支持m3u播放列表的播放器内就好啦，因为其中保存的是相对位置文件位置，请不要更改该课件的文件结构哦，否则该列表会失效的哦
7. 请修改IgnoreOptions.txt（仅支持True和False），True则为自动使用上次配置，否则每次都会询问
8. 近期版本更迭较大，测试并不全面，如有bug产生，请尽快联系我（Q:2537625460）
9. CSDN处仅提供1.5版本，由于本人一直在用，所以会持续更新，逐渐增加新功能，想获取新版本的可通过QQ联系我。另外本人尚处于初学阶段，欢迎大家加好友交流


# 更新日志：
## 版本号：1.6
## 发布日期：2018.
## 内容：
1. 本版本起，本项目托管于GitHub
2. 修改概览文件换行符，解决排版错乱问题
3. 新增getCourseJSON接口，方便以后远程调用

## 版本号：1.5
## 发布日期：2018.06.30（CSDN）：
## 内容：
1. 合并Easyload.py与Easyload2.py，仅保留新版本
2. 对预设值进行优化
    >（根据对已‘订阅’下载的15门课程各类课件大小进行统计，得到平均值如下：
    >    * video：94.81MB
    >    * pdf：0.61MB
    >    * 附件：1.02MB）
3. 新增自动生成播放列表（Playlist.m3u）机制，以便按照顺序学习视频（就不用对照课程概览一个一个找啦）
4. 优化tid提取机制，同时增加往期课程下载功能（包括已关闭学期）
5. 支持多系统指向各自系统内路径（仅区分操作系统类型，不区分版本）
6. 将network_file、config放到siguretools中，以便各种实用小工具的独立开发
7. 增加询问忽略选项，若设置IgnoreOptions相应选项为忽略，且相应config内的设置内容通过审核，则跳过询问直接下载，以节省时间

## 版本号：1.4
## 发布日期：2018.06.19
## 内容：
1. 再再次修正因为课程名不规范导致的课件无法保存问题（'\t'）-_-||
2. 修改Config类，增加分隔符的自定义
3. 优化课程概览中文件名存在换行（符）的问题
4. 修改json.load(r)传入的参数为str，使得linux系统下也可以正常使用
5. 增加network_file模块，实现实时写入硬盘与断点续传，解决内存占用过大问题
6. 对无内容和大小与网络标识大小不符的文件从断点开始续传
7. 增加文件预设值检测，在请求网络文件前先与预设值比对，如小于预设值，则请求网络文件，以优化此次更新带来的速度降低情况，预设值大小尚待优化
8. 由于本版本尚不稳定，断点续传功能暂时实现在Easyload2中，Easyload仅做1234项优化

## 版本号：1.3
## 发布日期：2018.06.05
## 内容：
1. 支持爱课程账号登录，如无爱课程账号，可在账号处输入'sharing'使用内置共享账号（密码随意）
2. 重写50%以上代码，将每个课件单元的所有信息写在一个类中，以便支持更多拓展功能
3. 主程序更名为Easyload以便加GUI时候调用
4. 在支持视频，文档下载的基础上增加富文本下的附件下载功能
5. 由于代码结构重构，有可能出现旧bug重现现象或者带来新的bug，但暂时流量不多，不太方便做全方位测试，请尽量注意提示信息，如有bug出现请先使用旧版本下载，并尽快联系我
6. 修正课程周次错位一个的问题
7. 概览文件增加文件类型头
8. 更新预告：GUI（界面）、下载失败文件报告、日志文件、课程订阅

## 版本号：1.2
## 发布日期：2018.05.27
## 内容：
1. 增加请求发生错误重新连接机制
2. 再次修正因为课程名不规范导致的课件无法保存问题（'\n'）
3. 增加课程下载完成后对未下载课件的审核机制（单进程）
4. 将下载信息提示符修改为信息提示头
5. 修改引导部分提示信息，唔……具体内容请自行体验~
6. 修改download参数中url为courseware（问题8主要来源）
7. 优化课程概览文件排版
8. 优化由于多次获取课程名导致的卡顿问题及其带来的错误问题

## 版本号：1.1
## 发布日期：2018.05.26
## 内容：
1. 修复由于课程名不规范导致的课件无法保存问题
2. 优化内部代码结构
3. 增加下载信息提示符
4. 将进程数放在config.txt中，请根据自己机器进行调整（运行一次后才能看到该文件）
5. 在课程根目录下增加课程概览文件
6. 重新修正因为课程名不规范导致的课件无法保存问题（'\/"|:*?<>'）
7. 修正因为config数据类型不匹配导致的修改进程数后自动回改的问题
8. 增加高清晰度资源缺失时自动降低画质机制

## 版本号：1.0
## 发布日期：2018.05.24
## 内容：
1. 实现对MOOC视频与课件的爬取
2. 增加多进程
3. 增加下载路径确认选项
4. 修复超清视频无法下载的问题
5. 由于暂时无法使用其他账号，将登陆步骤注释掉

### By Sigure_Mo
