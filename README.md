# Android_Hotfix
**Android热更新之dx工具jar转换dex**

主要记录 java->class->jar->dex 步骤的实现
此过程要使用JDK1.6，使用JDK1.7会报错，我遇到如下错误：
```
trouble processing:    
bad class file magic (cafebabe) or version (0033.0000)    
...while parsing Hello.class    
...while processing Hello.class    
1 warning    
no classfiles specified   
```


坑了好久。

android_dx工具.rar是Android热更新java->class->jar->dex中jar转换成dex所需的库，解压后放在Android SDK的platform-tools目录下即可，注意使用JDK1.6。
<br>不扯淡，具体步奏如下：
<br> 1. java->class, cmd进入java源码目录下， [javac -source 1.6 -target 1.6 com/package1/*.java com/package2/*.java]；
<br> 2. class->jar, [jar cvf abc.jar com/package1/*.class com/package2/*.class]；
<br> 3. jar->dex, [dx --dex --output ***/abc.jar ***/abc_dex.jar], ***是abc.jar的绝对路径；
<br> 4. 完成


**参考**
 http://blog.csdn.net/lmj623565791/article/details/49883661
