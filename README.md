# return-to-libc-attack
a simple return-to-libc attack example

tips:
  (1) 32 bit Linux Platform
  (2) you need to be root,and run "sysctl -w kernel.randomize_va_space=0" to shut the random space down
  (3) export MYSH=/bin/sh to tell the getenv the vaiable value(it's a way to pass paramters)
  (4) chmod 4777 retlib (you need to be root)
  (5) run getenv.c first to get the "/bin/bash" address,and use the value to alter exploit.c and run it.run the retlib at last.you'll see the "$" indicator for root.
  
tips(chinese version):

运行条件：
(1) 32位Linux平台
(2)切换root用户 运行 sysctl -w kernel.randomize_va_space=0 （禁用随机栈空间）
(3)在当前bash中export 一个环境变量 例如 export MYSH=/bin/sh (这个环境变量在程序中是向system提供参数用的)
(3) 使用 gcc -z execstack -fno-stack-protector retlib.c -o retlib 编译retlib.c （root用户）
(4) chmod 4777 retlib (root 用户)
(5)先运行getenv程序，得到/bin/sh字符串地址，修改exploit程序，(下面代码中数值已经填充好)，编译、运行exploit 程序，然后运行retlib ， 可以看到bash提示符，并且当前用户为root

Thanks to http://www.cis.syr.edu/~wedu/seed/labs.html SEED project!!!
