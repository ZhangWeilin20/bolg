# jetbrains 激活
1.输入下面网址，选其中最快的网址进去，下载 jetbra.zip

https://3.jetbra.in/

2.解压，放在对应目录/opt/module/JetBrains/，打开idea的bin目录下的idea64.vmoptions 文件,末尾追加
```
-javaagent:/opt/module/JetBrains/jetbra/ja-netfilter.jar=jetbrains
--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
```
