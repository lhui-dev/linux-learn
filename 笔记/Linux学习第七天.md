## 事件日期类 ##

   # date指令-显示当前日期 #

   * 基本语法
	1. date （功能描述：显示当前时间）
	2. date + %Y （功能描述：显示当前年份）
	3. date + %m （功能描述：显示当前月份）
	4. date + %d （功能描述：显示当前是哪一天）
	5. date "+%Y-%m-%d %H:%M:%S" (功能描述：显示年月日时分秒)

   * 应用实例
   * 案例1：显示当前时间信息
     指令：date

   * 案例2：显示当前时间年月日
     指令：date "+%Y-%m-%d"
   * 案例3：显示当前时间年月日时分秒
     指令：date "+%Y-%m-%d %H:%M:%S"


   # date指令-设置日期  #

   * 基本语法
	 date -s 字符串时间

   * 应用案例
    案例1：设置系统当前时间，
     比如 date "2020-11-11 11:11:11" 
   
   
   * cal 指令
     -查看日历指令
  
   * 基本语法
        cal [选项] （功能描述：不加选项，显示本月日历）

   * 应用实例
   
        案例1：显示当前日历： cal
        案例2：显示2021年日历 ： cal 2021




## 搜索查找类 ##


   # find指令 #

    find指令将从指定目录下向下递归地遍历其各个子目录，将满足条件的文件或者目录显示在终端。

    * 基本语法 
      find [搜索范围] [选项]
       选项说明：
         -name <查询方式>   功能：按照指定的文件名查找模式查找文件
         -user <用户名>  功能：查找属于指定用户的所有文件
         -size <文件大小>  功能：按照指定的文件大小查找文件
     
     * 应用实例
         案例1：按文件名：根据名称查找/home目录下hello.txt文件
          指令：find /home -name hello.txt
         案例2：按照拥有者：查找/opt目录下，用户名为nobody的文件
          指令：find /opt -user nobody
         案例3：查找整个Linux系统下大于200M的文件（+n 大于， -n 小于 ，n 等于,单位：k，M，G)
             指令：find / -size +200M


    ## locate指令 ##
        locate指令可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。locate指令无需遍历整个文件西瑞烃，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时刻


       * 基本语法
         locate 搜索文件
       * 特别说明
          由于locate指令基于数据库查询，所以第一次运行前，必须使用updatedb指令创建locate数据库。

       * 应用实例
         案例：请使用locate指令快速定位hello.txt所在目录

        补充：which指令，可以查找某个指令在哪个目录下
           比如：查找ls指令在哪个目录下
                which ls



    ## grep指令和管道符号| ##
      grep 过滤查找，管道符号,"|"，表示将前一个命令的处理结果输出传递给后面的命令处理。

     * 基本语法
       grep [选项] 查找内容 源文件

     * 常用选项
        -n 功能：显示匹配行及行号
        -i 功能：忽略字母大小写
      
     * 应用实例
       案例：请在hello.txt文件中，查找"yes" 所在行，并且显示行号
        指令：grep -n "yes" /home/hello.txt 或者 cat /home/hello.txt | grep "yes"

## 压缩和解压类 ##
    
    #  gzip用于压缩文件， gunzip用于解压文件 #

    * 基本语法
     gzip 文件  （功能：压缩文件，只能将文件压缩为*.gz文件）
     gunzip 文件.gz （功能：解压文件指令）

    * 应用实例
      案例1：gzip压缩，将/home下的hello.txt文件进行压缩
       指令：gzip /home/hello.txt
      案例2：gunzip解压，将/home下的hello.txt.gz文件进行解压 
       指令：gunzip /home/hello.txt.gz


   # zip/unzip指令 #
       zip用于压缩文件，unzip用于解压文件，这个在项目打包发布中很有用
     
     * 基本语法
      zip 选项 XXX.zip 将要压缩的内容 (功能：压缩文件和目录的命令)
      unzip 选项 XXX.zip 将要解压的内容 （功能：解压文件）
 
     * zip常用选项
      -r：递归压缩，即压缩目录
     * unzip常用选项
      -d <目录>：指定解压文件后文件的存放目录

     * 应用实例
      案例1：将/home下的所有文件进行压缩成myhome.zip
       指令：zip -r myhome.zip /home/ [将home及其包含的文件和子文件都压缩] 
      案例2：将myhome.zip解压到/opt/tmp目录下
         mkdir /opt/tmp
       指令：unzip -d /opt/tmp /home/myhome.zip

   # tar指令 #
     tar指令是打包指令，最后打包的文件是.tar.gz的文件。
  
    * 基本语法
      tar [选项] XXX.tar.gz 打包的内容 （功能：打包目录，压缩后的文件格式.tar.gz）
    * 选项说明
     -c 功能：产生.tar打包文件
     -v 功能：显示详细信息
     -f 功能：指定压缩后的文件名
     -z 功能：打包同时解压
     -x 功能：解包.tar文件
  
    * 应用实例
      案例1：压缩多个文件，将/home/pig.txt和/home/cat.txt压缩成pc.tar.gz
        指令：tar -zcvf pc.tar.gz /home/pig.txt /home/cat.txt
      案例2：将/home的文件夹压缩成myhome.tar.gz
        指令：tar -zcvf home/myhome.tar.gz /home/
      案例3：将pc.tar.gz解压到当前文件
        指令：tar -zxvf pc.tar.gz
      案例4：将myhome.tar.gz解压到/opt/tmp2目录下
       指令： mkdir /home/tmp2
             tar -zxvf /home/myhome.tar.gz -C /opt/tmp2