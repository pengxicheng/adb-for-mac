# adb-for-mac
adb for mac
1.找到android sdk的本地路径，
adb命令在platform-tool下面,记为XXXX
我的路径是(/Applications/eclipse/android-sdk-mac_x86/platform-tools)
2.打开终端输入
touch .bash_profile
open -e .bash_profile 点回车
3.添加路径
.bash_profile打开了，我们在这里添加路径，
如果打开的文档里面已经有内容,我们只要之后添加;XXXX(注意前面一定要用分号隔开)，
如果是一个空白文档的话，我们就输入一下内容
export PATH=${PATH}:XXXX
保存，关掉这个文档，
4.终端输入命令 source .bash_profile
5.终端输入命令 adb点回车，如果未显示command not found，说明此命令有效，环境便亮设置完成。

adb devices
打印所有链接的模拟器或者设备

adb forward <local> <remote>
建立本机端口8000 转发到模拟器或者设备的9000端口

adb kill-servser<===>adb start-server
关闭adb服务<====>开启adb服务

adb connect
通过WiFi链接
1.首先先通过USB链接
2.然后使用adb devices 查看设备
3.adb tcpip 5555 重启TCP端口：5555
4.通过手机查看手机的ip地址并记录
5.adb connect ip：5555
6.拔掉USB线，你仍然可以访问到设备此时adb devices 查看的时候会显示ip

adb usb
以USB模式重启adb

adb install [option]<path>
adb install test.apk
adb install -l test.apk 锁定应用
adb install -r test.apk 替换现有的应用
adb install -t test.apk 允许测试包
adb install -s test.apk 安装在sd卡上
adb install -d test.apk 版本降级
adb install -p test.apk 部分应用安装

adb uninstall [options]<package>
adb uninstall com.test.app
adb uninstall -k com.test.app 删除应用后保留数据

adb shell pm list package [options]<filtes>
adb shell pm list packages
adb shell pm list packages -f 查看相关文件
adb shell pm list packages -d 显示被禁用的包
adb shell pm list packages -e 显示已启用的包
adb shell pm list packages -s 显示系统包
adb shell pm list packages -3 显示第三方包
adb shell pm list packages -i 显示已安装的包
adb shell pm list packages -u 也显示卸载的包
adb shell pm list packages —user <USER_ID> 用户空间

adb shell pm path <package>
adb shell pm path com.android.phone

adb shell pm clear <package>
adb shell pm clear com.test.abc 清楚应用数据、缓存

adb pull <remote>[local]
adb pull /sdcard/demo.mp4 下载/sdcard/demo.mp4到/platform-tools目录中
adb pull /sdcard/demo.mp4 e:\ 下载/sdcard/demo.mp4到e盘

adb push <local>[remote]
adb push test.apk /sdcard 将platform-tools/test.apk 复制到/sdcard

 adb push d:\test.apk /sdcard

adb shell ls
1.adb shell
2.ls
ls -a
ls -i
ls -s
ls -n
ls -R

adb shell cd

adb shell rm
adb shell rm -f
adb shell rm -r
adb shell rm -d
adb shell rm -i

adb shell mkdir
mkdir -m 777 /sdcard/tmp 设置权限
mkdir -p /sdcard/tmp 根据需要创建

adb shell touch
touch /sdcard/tmp/test.txt 可以显示 ls /sdcard/tmp

adb shell pwd 显示当前位置

adb shell cp
cp /sdcard/test.txt /sdcard/demo.txt 复制

adb shell mv
mv /sdcard/tmp /system/tmp 移动
mv /sdcard/tmp /sdcard/test 重命名

adb shell netstat 网络统计

adb shell ping www.baidu.com

adb shell netcfg 网络配置和管理

adb shell ip
ip -f inet addr show waln0 显示WiFi-IP地址

adb logcat
adb logcat :V 最低优先级只显示详细信息
adb logcat :D 只显示调试信息
adb logcat :I 只显示信息
adb logcat :W 只显示警告信息
adb logcat :E 只显示错误信息
adb logcat :F 只显示致命信息
adb logcat *:S 最高级别

 adb logcat -b radio 查看无线电或者电话相关的消息缓冲区
 adb logcat -b event 查看事件相关缓冲区
 adb logcat -b main 默认
 adb logcat -c 清除整个缓冲区并退出
 adb logcat -d 打印日志并退出
 adb logcat -f test.logs 将日志信息写入test
 adb logcat -g 打印日志缓冲区并退出
 adb logcat -n <count> 设置日志数量
 adb logcat -r <kbytes> 按字节数输出日志
 adb logcat -s 设置默认

 adb logcat -v brief 显示优先级和PID
 adb logcat -v process 显示PID
 adb logcat -v tag 显示优先级
 adb logcat -v raw 只显示原始日志信息
 adb logcat -v time 显示日期、时间、优先级、PID
 adb logcat -v threadtime 显示日期、时间、优先级、PID、TID
 adb logcat -v long 显示所有字段并用空格分隔

adb shell dumpsys
dumps system data
adb shell dumpsys battery 注：安卓5.0
adb shell dumpsys batterystats 收集电池数据
adb shell dumpsys batterystats —reset 擦出就数据
adb shell dumpsys activity
adb shell dumpsys gfxinfo com.android.phone measuring com.android.phone ui performance

adb shell dumpstate
adb shell dumpstate > state.logs 保存存储状态到文件

adb shell screencap <filename>
adb shell screencap /sdcard/screen.png
adb pull /sdcard/screen.png

adb shell screenrecord 安卓4.4
adb shell screenrecord /sdcard/demp.mp4
adb pull /sdcard/demo.mp4

 adb shell screenrecord —size <width*height> 控制视频尺寸
 adb shell screenrecord —bit-rate <rete> 设置视频比特率
 adb shell screenrecord —time-limit <time>  单位：秒 设置视频时间 默认为180秒
 adb shell screenrecord —rotate 旋转90度
 adb shell screenrecord —verbose 在屏幕上显示日志和命令行

adb root 以root用户身份运行

adb sideload <update.zip>

adb shell ps
ps -p

adb shell top 显示CPU的进程
top -t 显示线程代替进程

adb shell getprop

adb shell set prop

文／风雨byt（简书作者）
原文链接：http://www.jianshu.com/p/2ee1efad7790
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。
