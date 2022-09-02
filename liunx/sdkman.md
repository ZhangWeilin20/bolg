# SDKMAN!使用指南

1.安装

在终端中输入以下命令进行安装:
```
$ curl -s "https://get.sdkman.io" | bash
```
如果提示缺少zip或unzip,安装后再次执行上面的命令即可.
```
安装需要的组件,Ubuntu为例
$ apt install zip
$ apt install unzip
安装需要的组件,archlinux为例
$ yay -S zip
$ yay -S unzip
```
安装完成后,在终端中输入:
```
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
```
输入以下命令查看安装情况:
```
$ sdk version
# 以下为输出
==== BROADCAST =================================================================
* 09/01/18: Gradle 4.5-rc-1 released on SDKMAN! #gradle
* 06/01/18: sbt 1.1.0 released on SDKMAN! #scala
* 20/12/17: Gradle 4.4.1 released on SDKMAN! #gradle
================================================================================

SDKMAN 5.6.0+287
```
2.安装到自定义位置

SDKMAN的默认安装位置为:$HOME/.sdkman.你可以通过设置SDKMAN_DIR环境变量来修改安装位置:

```
$ export SDKMAN_DIR="/opt/module/sdkman" && curl -s "https://get.sdkman.io" | bash
```
3.Beta通道

SDKMAN的Bate版,包含一些cli的新功能,但是可能会不稳定.如果需要使用Bate版本,需要修改~/.sdkman/etc/config文件:
```
$ sdkman_beta_channel=true
```
然后打开一个终端执行:

```
$ sdk selfupdate force
```
如果不需要使用Bate版本了,将上面的配置修改为false,再执行一次更新即可.

4.卸载

SDKMAN!没有提供自动化的卸载方法,可以通过以下命令进行卸载:
```
tar zcvf ~/sdkman-backup_$(date +%F-%kh%M).tar.gz -C ~/ .sdkman
$ rm -rf ~/.sdkman
```
然后从.bashrc，.bash_profile和/或.profile文件中编辑和删除初始化代码片段。如果您使用ZSH，请将其从.zshrc文件中删除。要删除的代码片段如下所示：

```
#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
[[ -s "/home/dudette/.sdkman/bin/sdkman-init.sh" ]] && source "/home/dudette/.sdkman/bin/sdkman-init.sh"
```
5.使用

5.0 列出支持的软件
```
$ sdk list
# 执行命令后进入vi模式进行阅读,q退出阅读
```
5.1 列出软件的版本
```
$ sdk list gradle

================================================================================
Available Gradle Versions
================================================================================
     4.5-rc-1             4.2.1                3.1                  2.11           
 > * 4.4.1                4.2-rc-2             3.0                  2.10           
     4.4-rc-6             4.2-rc-1             2.9                  2.1            
     4.4-rc-5             4.2                  2.8                  2.0            
     4.4-rc-4             4.1                  2.7                  1.9            
     4.4-rc-3             4.0.2                2.6                  1.8            
     4.4-rc-2             4.0.1                2.5                  1.7            
     4.4-rc-1             4.0                  2.4                  1.6            
     4.4                  3.5.1                2.3                  1.5            
     4.3.1                3.5                  2.2.1                1.4            
     4.3-rc-4             3.4.1                2.2                  1.3            
     4.3-rc-3             3.4                  2.14.1               1.2            
     4.3-rc-2             3.3                  2.14                 1.12           
     4.3-rc-1             3.2.1                2.13                 1.11           
     4.3                  3.2                  2.12                 1.10           

================================================================================
+ - local version
* - installed
> - currently in use
================================================================================
```
5.2 安装gradle
```
$ sdk install gradle

Downloading: gradle 4.4.1

In progress...

######################################################################## 100.0%

Installing: gradle 4.4.1
Done installing!

Setting gradle 4.4.1 as default.
```
5.3 安装指定版本软件
```
# 后面跟上版本号即可
$ sdk install gradle 4.4.1
```
5.4 安装本地包
```
$ sdk install groovy 3.0.0-SNAPSHOT /path/to/groovy-3.0.0-SNAPSHOT
```

5.5 卸载包
```
$ sdk uninstall scala 2.11.6
```

5.6 选择版本
```
选择一个版本用于当前终端:

$ sdk use scala 2.12.1
```
5.7 设置默认版本
```
$ sdk default scala 2.11.6
```
5.8 查看当前使用的版本
```
$ sdk current java
Using java version 8u111

#查看所有本地包的当前版本
$ sdk current
Using:
groovy: 2.4.7
java: 8u111
scala: 2.12.1
```
5.9 sdk版本升级
```
$ sdk upgrade springboot
Upgrade:
springboot (1.2.4.RELEASE, 1.2.3.RELEASE < 1.2.5.RELEASE)

# 本地所有sdk全部升级
$ sdk upgrade
Upgrade:
gradle (2.3, 1.11, 2.4, 2.5 < 2.6)
grails (2.5.1 < 3.0.4)
springboot (1.2.4.RELEASE, 1.2.3.RELEASE < 1.2.5.RELEASE)
```
5.10 离线模式
```
$ sdk offline enable
Forced offline mode enabled.

$ sdk offline disable
Online mode re-enabled!
当电脑没有网的时候,离线模式会进行自动切换.
```

5.11 SDKMAN!版本升级
```
$ sdk selfupdate

# 强制重新安装
$ sdk selfupdate force
```
