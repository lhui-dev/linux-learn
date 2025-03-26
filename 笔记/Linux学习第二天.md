
# 1.安装vm 和CentOS
    说明:
		学习Linux需要一个环境，我们需要创建一个虚拟机，然后在虚拟机上安装一个CentOS系统来学习

  		 	# 1.先安装virtual machine version

       		*1.先在官网下载VMware安装包。可以去官网找到最新版本是16.0.
       		*2.安装VMware之前先打开电脑的cpu虚拟化设置。也可以访问https://www.nocmd.com/windows/740.html查看相关教程。

                 #（1） 设置BIOS|CPU虚拟化设置
					1.选择重启你的电脑或者笔记本
                    2.一直按F2或者Fn+F2进入BIOS设置
					3.选择security下面的virtual technology 将其设置为enable
					4.按F10保存后退出即可
                    
              
            *3.设置完成之后重启电脑。
            *4.安装一直点击下一步即可
            *5.16.0版本的激活码（选择任意其中一个即可）
            	 ZF3R0-FHED2-M80TY-8QYGC-NPKYF
				 YF390-0HF8P-M81RQ-2DXQE-M2UT6
				 ZF71R-DMX85-08DQY-8YMNC-PPHV8
            *6.启动即可

   			# 2.再安装Linux（CentOS）

 
 
 	   	    # 3.原理示意图

#2.虚拟机克隆#  
     
   
   方式一：直接拷贝一份安装好的虚拟机文件
   方式二：使用VMware的克隆操作，注意克隆时，需要先关闭Linux系统。





#3.虚拟机的快照#

       
  ** 假如在使用Linux虚拟机系统的时候，你想回到原先的某一个状态，也就是说你担心可能有些误操作导致系统异常，需要回到某个原先正常运行的状态，VMware也提供了此功能，就是快照管理。

     应用实例
		1.安装好系统后，先做一个快照A
        2.进入到系统，创建一个文件夹，再保存一个快照B
        3.回到系统刚刚安装好的状态，即快照A
        4.试试看，是否还能再次回到快照B
        5.示意图
		

#4.虚拟机的迁移和删除#


   #1. 迁移

       把虚拟系统这个文件整体拷贝或者剪贴到另外位置使用。
  
   #2. 删除
       
      用VMware进行移除，在从磁盘删除即可。或者直接手动删除虚拟机系统对应的文件夹即可。
       


#5.安装vmtools
   
   1.安装vmtools后，可以让我们在Windows下更好的管理vm虚拟机
   2.可以设置Windows和centos的共享文件夹

    
      #安装vmtools的步骤
     
       1.进入centos
       2.点击vm菜单的->install VMware tools
       3.centos会出现一个vm的安装包，xx.tar.gz
       4.拷贝到/opt
            鼠标右键打开终端
       5.使用解压命令tar，得到一个安装目录
          	cd/opt [进入到opt目录]
            tar -zxvf VMwareTools-10.3.22-15902021.tar.gz
       6.进入该vm解压的目录下，/opt目录下
            cd vmware...
       7.安装
           使用命令 ./vmware-install.pl
       8.全部使用默认设置即可，就可以安装成功
       9.注意：安装vmtools需要有gcc
           查看是否安装了gcc命令： gcc -v

      #示意图 



#6.设置共享文件夹#
     
    # 1.基本介绍
       1.为了方便，可以设置一个共享文件夹，比如D:/myshare

  
    # 2.具体步骤
        1.菜单->vm->setting，如图设置即可
         注意:设置选项为always enable，这样可以读写了
        2.Windows和centos可共享 D:/myshare目录可以读写文件了
        3.共享文件夹在centos的/mnt/hgfs/下

    # 3.注意事项和细节说明
         *1. Windows 和centos就可以共享文件了，但是实际开发中，文件的上传和下载是需要使用远程方式完成

         *2.远程方式登陆 待补充。。。

     