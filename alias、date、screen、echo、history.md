# Basic-command
# __别名__  
 
永久修改用户的别名的路径  

/etc/bashrc   所有用户  
~/.bashrc     当前用户 

配置完成后必须要输入  

. /etc/bashrc或者source /etc/bashrc
. ~/bashrc或者source ~/.bashrc  

这样配置才会生效  

如果想要执行原来的命令而不是别名需要如下四种姿势：  

\命令  
“命令”  
‘命令’  
command  命令


alias  查看所有的别名  
unalias ls  取消ls的别名  

# __日期和时间__

type date  可知date是外部命令，所以我们可以用

查看到date是外部命令，所以我们可以用查找外部命令的方式  
date --help  
info date  

内核时间，系统时间    
设置格式  月日时分年秒  
date -s  设置时间  
date -d  显示时间  
后面常接  
“-1 day”  
+“%F %T”  
+%s  显示出一串距离unix元年也就是1970年距今的秒数如果按照人类便于读取的方式显示出来的命令是date -d @$(date +%s)=date -d “date +%s”=date  
+%w  显示出数字的周几

硬件时间，主板时间clock  
clock -s 硬件时间是老大  
clock -w 内核时间是老大  
  
设置时区的方式是    

centos 6  
tzselect 中国境内按下的数字顺序一般是5，9，1，1  

centos 7  
timedatectl set-timezone Asia/Shanghai把时区设置为上海  
timedatectl status查看当前的时区  
timedatectl list-timezones  列出时区

natdate 192.18.254.250  向192.168.254.250的主机获取时间并设置为系统时间   


poweroff 关机并断电  
shutdown -h now 马上断电关机   
suhtdown 10：30  10点30关机 
shutdown -c 取消刚刚的关机指令  
reboot  重启计算机


# __远程救援__  

screen -S 名字  创建一个名为”名字“的救援会话  

screen -x 名字   进入一个 名为”名字“的救援会话中  

screen -ls  查看当前有哪些救援会话   

screen -r  恢复之前退出的救援会话  

ctrl+a，再按下d   个人退出救援会话  

exit   全部人一起退出救援会话  

# __echo__  

echo -e 

\a   发出警告声   

\0   插入八进制所代表的ASCII字符   
  echo -e   
'\033[43;31;5mmagedu\033[0m'=echo -e '\e[43;31;5m你好\e[0m'  
阿斯科码表中e可以转换成33

\x  插入十六进制所代表的ASCII字符  

echo '---' > /sys/class/scsi_host/host0/scan  虚拟机中添加硬件设备的额命令

## __想知道ascii表的表示方式?__  
先输入whatis acsii 或者whereis ascii

从得出的信息中可以知道查看man 7可以查看，所以我们输入  
man 7 ascii 

# __反引号、$()和双引号、单引号、大括号的区别__

反引号（在esc的下方的那个键,英文模式的输入法才能按的出来）：变量和命令全部都能识别，优先执行  
$(): 同上  
双引号：只能识别变量无法识别命令  
单引号：无法识别变量和命令  
大括号：按规律列举字符  
Tab键：按两下总是会有惊喜  

# __历史__  
存放修改历史的路径是~/.bash_history或 /etc/profile中

history -c 清除历史  
history -d 名字  清除某个命令的历史   
history -s 伪造历史      
history -a  把磁盘中的历史写进内存中  
history -r  把硬盘中的历史有重复的加进内存的历史中    
history -n 把硬盘中的历史无重复的加进内存的历史中  
history -p  隐藏历史（这个选项学问有点多）  

HISTSIZE：命令历史记录的条数    

HISTFILE：指定历史文件，默认为~/.bash_history    

HISTFILESIZE：命令历史文件记录历史的条数    

HISTTIMEFORMAT=“%F %T “ 显示时间  

HISTIGNORE=“str1:str2*:… “ 忽略str1命令，str2开头的历史    

控制命令历史的记录方式：    

环境变量：HISTCONTROL    

ignoredups 默认，忽略重复的命令，连续且相同为“重复”  

ignorespace 忽略所有以空白开头的命令    

ignoreboth 相当于ignoredups, ignorespace的组合    

erasedups 删除重复命令    

export 变量名="值“    

!his   以什么开头his开头的命令  
!?history   包含history的命令  
!:p   仅打印  


!string 重复前一个以“string”开头的命令  
!?string 重复前一个包含string的命令  
!string:p 仅打印命令历史，而不执行  
!$:p 打印输出 !$ （上一条命令的最后一个参数）的内容  
!*:p 打印输出 !*（上一条命令的所有参数）的内容  
^string 删除上一条命令中的第一个string  
^string1^string2 将上一条命令中的第一个 string1替换为string2  
!:gs/string1/string2 将上一条命令中所有的string1都替换为 string2  


bash的快捷键  

ctrl+a，e，u，k，c，z，xx，o，r,g,y

esc,.=alt+.  

alt+r  
alt+N
