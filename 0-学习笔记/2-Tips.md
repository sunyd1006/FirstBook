# 小Tips


# 熟悉Mac电脑
常见的开发环境，安装说明
如何安装Iterm2（替代Mac自带的终端）：
- 如何安装brew：https://zhuanlan.zhihu.com/p/90508170
  > mac安装brew、wget、node、nvm
  Iterm设置System-wide的快捷打开命令：https://www.zhihu.com/question/20692634，用的Automator.app

- 如何安装oy-my-sh：https://www.jianshu.com/p/ba08713c2b19
  https://a1049145827.github.io/2019/05/15/Mac-%E7%8E%AF%E5%A2%83%E5%AE%89%E8%A3%85%E5%B9%B6%E9%85%8D%E7%BD%AE%E7%BB%88%E7%AB%AF%E7%A5%9E%E5%99%A8-oh-my-zsh/

  
如何安装 Maven3.3.9：在开发机上，找到 ~/tools/maven-----3.3.9-bin.tar.gz的文件夹，复制到 workspace目录，就可以在mac本地同步下载对应的文件啦。
如何安装 Scala2.11.8：同上，在开发机上下载源码包，如何配置Scala本地的环境变量
如何安装 Spark：我在本地使用开发机上的环境，无效。故取官网下载到了带 hadoop版本的环境，并非和小组同步。
如何安装 Protobu2.4.1：（以及解决报错errors generated. make[2]: *** [message.lo] Error 1 make[1]: *** [all-recursive] Error 1 make: *** [all] Error 2）：

> 安装的链接：https://www.jianshu.com/p/67f64307d268，重点（会报错报错请看）：https://blog.csdn.net/delphiwcdj/article/details/38460529
>



Mvn：改镜像为阿里云：https://zhuanlan.zhihu.com/p/71998219




## 更新 Github hosts域名，效果并不好

github访问太慢：https://segmentfault.com/a/1190000022697560

1. 执行java -jar程序
2. http://localhost:8880/
3. sudo vim /etc/hosts
4. sudo killall -HUP mDNSResponder




## VsCode好用的插件

VSCode好用的插件：

- Chinese
- zhihu 插件


### VIM

```txt
gg: 行首
G: 行尾

^: 行首 
$: 行尾
```

