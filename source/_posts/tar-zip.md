---
title: Linux下压缩某个文件夹命令
date: 2018-01-31 00:50:49
tags:
---
tar -zcvf /home/xahot.tar.gz /xahot
tar -zcvf 打包后生成的文件名全路径 要打包的目录
例子：把/xahot文件夹打包后生成一个/home/xahot.tar.gz的文件。
zip 压缩方法：
 
压缩当前的文件夹 zip -r ./xahot.zip ./* -r表示递归
zip [参数] [打包后的文件名] [打包的目录路径]
解压 unzip xahot.zip 不解释
linux zip命令的基本用法是：
 
linux zip命令参数列表：
 
-a 将文件转成ASCII模式
-F 尝试修复损坏的压缩文件
-h 显示帮助界面
-m 将文件压缩之后，删除源文件
 
-n 特定字符串 不压缩具有特定字尾字符串的文件
-o 将压缩文件内的所有文件的最新变动时间设为压缩时候的时间
-q 安静模式，在压缩的时候不显示指令的执行过程
-r 将指定的目录下的所有子目录以及文件一起处理
-S 包含系统文件和隐含文件（S是大写）
-t 日期 把压缩文件的最后修改日期设为指定的日期，日期格式为mmddyyyy
 
举例：
 
将/home/wwwroot/xahot/ 这个目录下所有文件和文件夹打包为当前目录下的xahot.zip
 
zip –q –r xahot.zip /home/wwwroot/xahot
 
上面的命令操作是将绝对地址的文件及文件夹进行压缩.以下给出压缩相对路径目录
 
比如目前在Bliux这个目录下,执行以下操作可以达到以上同样的效果.
 
zip –q –r xahot.zip xahot
 
比如现在我的xahot目录下,我操作的zip压缩命令是
 
zip –q –r xahot.zip *
 
以上是在安静模式下进行的，而且包含系统文件和隐含文件
//////////////////////////////////////////////////////////
unzip语 法：
 
unzip [-cflptuvz][-agCjLMnoqsVX][-P <密码>][.zip文件][文件][-d <目 录>][-x <文件>] 或 unzip [-Z]
 
补充说明：unzip为.zip压缩文件的解压缩程序。
 
unzip参 数：
-c 将解压缩的结果显示到屏幕上，并对字符做适当的转换。
-f 更新现有的文件。
-l 显示压缩文件内所包含的文件。
-p 与-c参数类似，会将解压缩的结果显示到屏幕上，但不会执行任何的转换。
-t 检查压缩文件是否正确。
-u 与-f参数类似，但是除了更新现有的文件外，也会将压缩文件中的其他文件解压缩到目录中。
-v 执行是时显示详细的信息。
-z 仅显示压缩文件的备注文字。
-a 对文本文件进行必要的字符转换。
-b 不要对文本文件进行字符转换。
-C 压缩文件中的文件名称区分大小写。
-j 不处理压缩文件中原有的目录路径。
-L 将压缩文件中的全部文件名改为小写。
-M 将输出结果送到more程序处理。
-n 解压缩时不要覆盖原有的文件。
-o 不必先询问用户，unzip执行后覆盖原有文件。
-P<密码> 使用zip的密码选项。
-q 执行时不显示任何信息。
-s 将文件名中的空白字符转换为底线字符。
-V 保留VMS的文件版本信息。
-X 解压缩时同时回存文件原来的UID/GID。
[.zip文件] 指定.zip压缩文件。
[文件] 指定要处理.zip压缩文件中的哪些文件。
-d<目录> 指定文件解压缩后所要存储的目录。
-x<文件> 指定不要处理.zip压缩文件中的哪些文件。
-Z unzip -Z等于执行zipinfo指令
 
举例：
 
将/home/wwwroot/xahot.zip解压到当前目录
 
unzip xahot.zip
 
如果出现这个提示：
-bash: zip: command not found    不能执行ZIP压缩，是因为没有安装ZIP，
运行下这条安装命令即可  yum install zip

===============================================================

 

# tar -cvf /usr/local/auto_bak/test.tar /usr/local/test 仅打包，不压缩 
# tar -zcvf /usr/local/auto_bak/test.tar.gz /usr/local/test 打包后，以gzip压缩 在参数f后面的压缩文件名是自己取的，习惯上用tar来做，如果加z参数，则以tar.gz 或tgz来代表gzip压缩过的tar file文件
解压操作:
#tar -zxvf /usr/local/test.tar.gz
tar 解压缩命令详解
-c: 建立压缩档案

-x：解压
-t：查看内容
-r：向压缩归档文件末尾追加文件
-u：更新原压缩包中的文件

这五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。下面的参数是根据需要在压缩或解压档案时可选的。

-z：有gzip属性的
-j：有bz2属性的
-Z：有compress属性的
-v：显示所有过程
-O：将文件解开到标准输出

下面的参数-f是必须的

-f: 使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。

# tar -cf all.tar *.jpg 
这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文件名。

# tar -rf all.tar *.gif 
这条命令是将所有.gif的文件增加到all.tar的包里面去。-r是表示增加文件的意思。

# tar -uf all.tar logo.gif 
这条命令是更新原来tar包all.tar中logo.gif文件，-u是表示更新文件的意思。

# tar -tf all.tar 
这条命令是列出all.tar包中所有文件，-t是列出文件的意思

# tar -xf all.tar 
这条命令是解出all.tar包中所有文件，-x是解开的意思

压缩

tar –cvf jpg.tar *.jpg //将目录里所有jpg文件打包成tar.jpg

tar –czf jpg.tar.gz *.jpg   //将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一  个gzip压缩过的包，命名为jpg.tar.gz

tar –cjf jpg.tar.bz2 *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2

tar –cZf jpg.tar.Z *.jpg   //将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z

rar a jpg.rar *.jpg //rar格式的压缩，需要先下载rar for linux

zip jpg.zip *.jpg //zip格式的压缩，需要先下载zip for linux

解压

tar –xvf file.tar //解压 tar包

tar -xzvf file.tar.gz //解压tar.gz

tar -xjvf file.tar.bz2   //解压 tar.bz2

tar –xZvf file.tar.Z   //解压tar.Z

unrar e file.rar //解压rar

unzip file.zip //解压zip

总结
  (1)、*.tar 用 tar –xvf 解压
  (2)、*.gz 用 gzip -d或者gunzip 解压
  (3)、*.tar.gz和*.tgz 用 tar –xzf 解压
  (4)、*.bz2 用 bzip2 -d或者用bunzip2 解压
  (5)、*.tar.bz2用tar –xjf 解压
  (6)、*.Z 用 uncompress 解压
  (7)、*.tar.Z 用tar –xZf 解压
  (8)、*.rar 用 unrar e解压
  (9)、*.zip 用 unzip 解压