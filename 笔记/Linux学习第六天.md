# 第九章- 实用指令 #

	## 1.指令运行级别 ##

    *基本介绍
   
	      运行级别说明：
	          
	      0：关机
	      1：单用户【找回丢失密码】
	      2：多用户状态没有网络服务
	      3：多用户状态有网络服务
	      4：系统未使用保留给用户
	      5：图形界面
	      6：系统重启
	
	     常用运行级别是3和5，也可以指定默认运行级别


    *应用实例
      	 命令： init[0123456]

    *应用案例：
      	 通过init来切换不同的运行级别，比如5-3，然后关机



   ## 2.指定运行级别 ##

    * CentOS7后运行级别说明
         在centos7以前，在/ect/inittab文件中进行了简化，如下
         multi-user.target:analogous to runlevel 3
         graphical.target:analogous to runlevel 5


       # To view current default target,run:
         systemctl get-default

       # To set a default target,run:
         systemctl set-default graphical.target



   ## 3.找回root密码 ##

    ** 面试题 **

	      如何找回root密码（CentOS7.6以后）
	
	       1.首先，启动系统，进入开机界面，在界面中按"e"进入编辑界面
	       2.进入编辑界面，使用键盘啥上的上下键把光标往下移动，找到以"Linux16"开头内容所在的行数，在行的最后面输入： init=/bin/sh
	       3.接着，输入完成后，直接快捷键:Ctrl+x 进入单用户模式。
	       4.接着，在光标闪烁的位置中输入： mount -o remount,rw / (注意：各个单词之间有空格)，完成之后按键盘的回车键
	       5.在新的一行最后面输入passwd，完成后按键盘的回车键。输入密码，然后再次确认密码即可，密码修改成功后，会显示passwd...的形式，说密码修改成功。 
	       6.接着，在鼠标闪烁的位置中（最后一行中）输入：touch /.autorelabel
	       （注意：touch与/后面有一个空格），完成之后按回车键。
	       7.继续在光标闪烁的位置中，输入： exec /sbin/init (注意：exec 与 / 后面有一个空格)，完成后按键盘的回车键，等待系统自动自改密码，过程时间可能有点长，完成后，系统会自动重启，新的密码生效了。
	       
	  
	
		    练习：
		    设置运行级别，Linux运行后，直接进入到命令行终端（3）
		    systemctl set-default multi-user.target






   ## 4.帮助指令 ##

    * man获得帮助信息
    * 
	      基本语法： man [命令或配置文件] （功能描述：获得帮助信息）
	
	      案例演示： 查看ls命令的帮助指令
	      指令： man ls
	      在Linux下隐藏文件是.开头      

    * help指令
    * 
	      基本语法： help 命令 （功能描述：获得shell内置命令的帮助信息）
	 
	      应用实例：
	        案例演示：查看cd命令的帮助信息
	        指令： help cd
	
	      百度帮助更直接！！！！



   ## 5.文件目录类  ##

    ** pwd 指令

	     基本语法： pwd （功能描述：显示当前工作目录的绝对路径）
	
	     应用实例：
	     案例 ：显示当前工作目录的绝对路径


    ** ls 指令
	     基本语法： ls [选项] [目录或者是文件]
	
	     常用选项：
	        -a :显示当前目录所有的文件和目录，包括隐藏的
	        -l :以列表的方式显示信息
	   
    ** cd 指令

	     基本语法：cd [参数] （功能描述：切换到指定目录）
	     理解：绝对路径和相对路径
	         绝对路径是从根目录开始
	         相对路径是根据当前位置开始
	     
	     cd ~ 或者 cd ： 回到自己的家目录，比如你是root， cd ~ 到 /root
	
	     cd .. 回到当前目录的上一级目录
	     

	    应用案例：
	
	
	    案例1：使用绝对路径切换到root目录 ，
	     指令： cd /root
	    案例2：使用相对路径到/root目录，比如在/home/tom
	     指令：cd ../../root
	    案例3：表示回到当前目录的上一级目录
	     指令：cd..
	    案例4：回到家目录
	     指令：cd ~
 

    ** mkdir 指令
       * mkdir指令用户创建目录

	        基本语法：mkdir [选项] 要创建的目录
	
	        常用选项：
	         -p ：创建多级目录


       * 应用实例
	        案例1：创建一个目录 /home/dog
	         指令：mkdir /home/dog
	        案例2：创建多级目录 /home/animal/tiger
	         指令：mkdir -p /home/animal/tiger


    ** rmdir 指令
	      * rmdir指令删除空目录
	  
	        基本语法：rmdir [选项] 要删除的空目录
	
	      * 应用实例
	        案例：删除一个目录/home/dog
	
	        使用细节：
	           rmdir删除的是空目录，如果目录下有内容时无法删除的。
	           提示：如果需要删除非空目录，需要使用 rm -rf 要删除的目录
	           例如：rm -rf /home/animal 注意：删除操作应谨慎！！



    ** touch指令
	         touch指令创建空文件
	        * 基本语法：    
	          touch 文件名称
	        * 应用实例：
	          案例：创建一个空文件夹 hello.txt



   ** cp指令 - 
	        cp指令拷贝文件到指定目录
	
		     * 基本语法：
		       cp [选项] source dest
		
		     * 常用选项
		       -r:递归复制整个文件夹
		
		     * 应用实例
		       案例1：将/home/hello.txt拷贝到 /home/bbb 目录下
               指令：cp hello.txt /home/bbb		  

		       案例2：递归复制整个文件夹，举例
               指令：cp -r /home/bbb/opt		 

		     * 使用细节
		       强制覆盖不提示的方法：\cp
               eg: \cp -r /home/bbb /opt

  
   ** rm指令
	 说明：rm指令移除文件或目录

         * 基本语法：
            rm [选项] 要删除的文件或目录

         * 常用选项
            -r：递归删除整个文件夹
            -f：强制删除不提示

         * 应用实例：
            案例1：将/home/hello.txt删除
            指令：rm /home/hello.txt
            案例2：递归删除整个文件夹/home/bbb
            指令：rm -r /home/bbb
         * 使用细节
            强制删除不提示的方法： 带上-f参数即可
             如：rm -rf /home/bbb
     
   ** mv指令
     说明：mv指令用来移动文件目录或者重命名

     * 基本语法：
         mv oldNameFile newNameFile  (功能描述：重命名)
 
         mv /temp/movefile/argetFolder （功能描述：移动文件）
 
     * 应用实例：
         案例1：将/home/cat.txt文件重命名为pig.txt
          指令： mv cat.txt pig.txt
         案例2：将/home/pig.txt文件移动到/root目录下
          指令： mv /home/pig.txt /root
         案例3：将/home/pig.txt文件移动到/root目录下并重命名为hh.txt
          指令： mv /home/pig.txt /root/hh.txt
         案例4：移动整个目录，比如将/opt/bbb移动到/home下
          指令： mv /opt/bbb /home




   ** cat 指令
       说明：cat指令用来查看文件内容

         * 基本语法：
          cat [选项] 要查看的文件
         
         * 常用选项：
          -n：显示行号

         * 应用实例：
          案例一： 查看/ect/profile文件内容，并显示行号
           指令：cat -n /etc/profile 
         
     
         * 使用细节：
           cat只能浏览文件，而不能修改文件，为了浏览方便，一般会加上 管道命令 | more
            例如：cat -n /etc/profile |more [进行交互]




   ** more 指令
          说明：more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more指令中内置了若干快捷键如下：

		              空格键    代表向下翻一页
		              enter键   代表向下翻一行
		              q         代表立刻离开more，不再显示该文件内容
		              Ctrl + f  代表向下滚动一屏
		              Ctrl + b  代表返回上一屏
		               =        代表输出当前行的行号
		               :f       代表输出文件名和当前的行号
        

        * 基本语法
          more 要查看的文件

        * 应用实例
          案例：采用more查看文件/etc/profile
           指令：more /etc/profile

 

   ** less 指令
          说明：less指令用来分屏查看内容，它的功能用与more指令相似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率。
              相关快捷键：
                  空格键  代表向下翻动一页
                  [pagedown] 代表向下翻动一页
                  [pageup]   代表向上翻动一页
                  /子串      代表向下搜寻[子串]的功能；n ：向下查找；N：向上查找
                  ？子串      代表向上搜寻[子串]的功能；n ：向上查找；N：向下查找
                  q          代表离开less程序


       基本语法
         less 要查看的文件
       应用实例：
        案例：采用less查看一个大文件/opt/...



   ** echo指令
        说明：echo指令用来输出内容到控制台

      
        * 基本语法
           echo 选项 输出内容

        * 应用实例
          案例1：使用echo指令输出环境变量比如： $PATH ,$HOSTNAME
            指令：echo $HOSTNAME
        
          案例2：使用echo指令输出hello，world！
            指令：echo hello，world！

    

 ** head指令
      说明：head指令用于显示文件的开头部分，默认情况下head指令显示文件的前10行内容。

        * 基本语法 
           head 文件  [功能描述:查看文件头10行内容]
           head -n 5 文件 [功能描述：查看文件头5行内容，5可以是任意行数]


        * 应用实例
           案例：
             查看/etc/profile的前5行代码
              指令：head -n 5 /etc/profile


 ** tail指令
        说明：tail指令用于输出文件尾部的内容，默认情况下显示文件前19行内容。
         
         * 基本语法
              1. tail 文件 功能描述：查看文件尾10行文件
              2. tail -n 5 文件 功能描述：查看文件尾5行内容，5可以是任意行数
              3. tail -f 文件 功能描述：实时追踪该文档的所有更新

          * 应用实例
             案例1：查看/etc/profile的最后5行代码
              指令：tail -n 5 /etc/profile
             案例：实时监控mydata.txt，看到文件有变化时，是否看到，实时追加的日期 
               指令： tail -f /home/madata.txt



** >指令和 >>指令
     说明： >指令用来输出重定向，  >>指令用来追加内容
                 
        * 基本语法
			1. ls -l > 文件   （功能描述：列表的内容写入到文件中【覆盖写】）
			2. ls -al >> 文件    （功能描述：列表的内容追加到文件的末尾）
			3. cat 文件1 > 文件2  （功能描述：将文件1的内容覆盖到文件2）
			4. echo “内容” >> 文件 （功能描述：追加内容） 


        * 应用实例
            案例1：将/home目录下的文件列表写入到/home/info.txt中
              指令：ls -l > /home/info.txt [如果info.txt没有，则会创建]
            案例2：将当前日历信息追加到 /home/mycal文件中
              注：cal用于显示当前日历信息
               指令：cal >> /home/mycal



** ln指令
    说明：ln指令也叫软链接指令也称为符号链接，类似于Windows里的快捷方式，主要存放了链接其他文件的路径

     * 基本语法
       ln -s [原文件或目录] [软链接名] （功能描述：给原文件创建一个软链接）

     * 应用实例
         案例1：在/home目录下创建一个软链接myroot，连接到/root目录
           指令：ln -s /home myroot
         案例2：删除软链接myroot
          指令：rm /home/myroot
     * 细节说明
          当我们使用pwd指令来查看当前目录时，仍看到的是软链接所在目录 
               
** history指令
     说明：history指令用来查看已经执行过的历史命令，也可以执行历史命令

     * 基本语法：
        history （功能描述：查看已经执行过的历史命令）
     * 应用案例：
        案例1：显示所有的历史命令
         指令：history
        案例2：显示最近使用过的10个指令
         指令：history 10
        案例3：执行历史编号为5的指令
         指令：!5


  