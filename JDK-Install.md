<h1 id="jdk0">JDK 安装</h1>

------

*   [JDK 安装](#jdk0)
    *   [CentOS 下过程](#jdk1)
    *   [资料](#jdk2)
    
------

<h2 id="jdk1">CentOS 下过程</h2>

- JDK 在 CentOS 和 Ubuntu 下安装过程是一样的，所以这里不再讲 Ubuntu 系统下的安装
- JDK 1.8 下载
 - 此时（20160205）最新版本：`jdk-8u72-linux-x64.tar.gz`
 - 官网：<http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html>
 - 官网压缩包地址：<http://211.138.156.198:82/1Q2W3E4R5T6Y7U8I9O0P1Z2X3C4V5B/download.oracle.com/otn-pub/java/jdk/8u72-b15/jdk-8u72-linux-x64.tar.gz>
 - 百度云下载（64 位）：<http://pan.baidu.com/s/1eQZffbW>


- 默认 CentOS 有安装 openJDK，建议先卸载掉
 - 检查 JDK 命令：`java -version`
 - 查询本地 JDK 安装程序情况； `rpm -qa|grep java`
   - 我查询出来的结果如下：
   ```
   java-1.6.0-openjdk-1.6.0.38-1.13.10.0.el6_7.x86_64
   java-1.7.0-openjdk-1.7.0.95-2.6.4.0.el6_7.x86_64
   tzdata-java-2015g-2.el6.noarch
   ```
   - 卸载上面三个文件（`--nodeps` 的作用：忽略依赖的检查）：
   - `sudo rpm -e --nodeps java-1.6.0-openjdk-1.6.0.38-1.13.10.0.el6_7.x86_64`
   - `sudo rpm -e --nodeps java-1.7.0-openjdk-1.7.0.95-2.6.4.0.el6_7.x86_64`
   - `sudo rpm -e --nodeps tzdata-java-2015g-2.el6.noarch`


- JDK 1.8 安装
    - 我们以安装 `jdk-8u72-linux-x64.tar.gz` 为例
    - 我个人习惯 `/opt` 目录下创建两个目录 `setups` 和 `program`。`setups` 用来存放各种软件安装包，`program` 用来存放各种解压后的软件包，下面的讲解也都是基于此习惯
    - 解压安装包：`sudo tar -zxvf jdk-8u72-linux-x64.tar.gz`
    - 配置环境变量：
        - 编辑配置文件：`sudo vim /etc/profile`
        - 在该文件的最尾巴，添加下面内容：
        ```
        JAVA_HOME=/opt/program/jdk1.8.0_72
        PATH=$PATH:$JAVA_HOME/bin
        CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
        export JAVA_HOME
        export PATH
        export CLASSPATH
        ```
        - 执行命令，刷新该配置（必备操作）：`source /etc/profile`
        - 检查是否使用了最新的 JDK：`java -version`


- 资料
 - <http://www.jikexueyuan.com/course/480_1.html?ss=1>
 