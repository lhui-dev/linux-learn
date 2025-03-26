# 用户管理 #


  ## 基本介绍 ##
   
   Linux系统是一个多用户多任务的操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。


    **添加用户**

     * 基本语法     useradd 用户名

     *应用案例 
     
      添加一个用户 milan 

     useradd milan
  
     * 细节说明

     1.当创建用户成功后，会自动的创建和用户同名的家目录
      在/home/milan。
       useradd milan

     2.也可以通过 useradd -d 指定目录 新的用户名 ，该新创建的用户指定家目录。
      useradd -d /home/test king  含义是创建一个名为King的用户其家目录在/home/test下


    ** 指定/修改密码 **
  
      * 基本语法* 
            passwd 用户名
 
      * 应用案例 

          给milan指定密码
          passwd milan 
 
          pwd指令 显示当前用户在哪个目录下


    ** 删除用户 **

      **基本语法
        userdel 用户名

      **应用案例
      1.删除用户milan，但是要保留家目录
         userdel milan

      2.删除用户以及用户主目录（此操作慎重！）    
		 userdel -r milan  
   


 
   ** 查询用户信息指令 **


     **基本语法
       id 用户名
   
     **应用实例
     1.查看root用户信息
       id root

     **细节说明
    当用户不存在时，返回无此用户
 

  
   ** 切换用户 **

      **介绍  su 即 switch user
        在操作Linux中，如果当前用户的权限不够，可以通过su - 指令，切换到高权限用户，比如root

      ** 基本语法
        su - 用户名
      
      **应用实例
       创建一个用户Jack，指定密码，然后切换到用户Jack

   
     **细节说明
       1.从权限高的用户切换到权限低的用户不需要输入密码，反之需要
       2.当需要返回到原来用户时，使用exit/logout指令



   
  ** 查看当前用户/第一次登录用户 ** 

     **基本语法
       whoami 或者 who am I/i 







   ** 用户组 **

     **介绍
      类似于角色，系统可以对有共性的多个用户进行统一的管理

     ** 新增组
      指令： groupadd 组名
     
     案例演示
     groupadd wudang
 
     **删除组
     指令： groupdel 组名

     案例演示
     groupdel wudang


     **增加用户时直接加上组
     指令： useradd -g 用户组 用户名

     案例演示
     增加一个用户 zwj，直接将他指定到 wudang
     指令：
          groupadd wudang
          useradd -g wudang zwj


     **修改用户的组
     指令： usermod -g 用户组 用户名

     案例演示
    创建一个组mojiao，把zwj放在mojiao这个组中
   
    ** 用户和组相关文件 **
 

     * /etc/passwd 文件 
     
       用户（user）的配置文件，记录用户的各种信息

       每行的含义： 用户名：口令：用户标识号：注释性描述：主目录：登录Shell

  
     *  /etc/shadow 文件
   
        口令的配置文件
    
        每行的含义： 登录名：加密口令：最后一次修改时间：最小间隔时间：最大时间间隔：警告时间：不活动时间：失效时间：标志

     *  /etc/group 文件
     *  
        组（group)的配置文件，记录Linux包含的组的信息

        每行含义： 组名：口令：组标识号：组内用户列表  
   
  
    