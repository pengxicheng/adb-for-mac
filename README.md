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

文／风雨byt（简书作者）
原文链接：http://www.jianshu.com/p/dfb8d753e9b3
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。
