# JavaFrameworkNotes
java各种框架学习的网址记录<br/>

Ehcache纯Java缓存框架：<br/>
http://blog.csdn.net/jingqiang521/article/details/48175977<br/>
http://raychase.iteye.com/blog/1545906<br/>

Redis与spring-data-redis整合(版本比较老的啦，spring-data-redis1.0.x, Jedis2.1.x)：<br/>
http://www.cnblogs.com/tankaixiong/p/3660075.html<br/>
Redis3.0与Jedis2.7.2 客户端与Spring整合:<br/>
http://blog.csdn.net/centre10/article/details/50761815<br/>

Redis、Ehcache、Memcached三个缓存框架：<br/>

Redis与Ehcache的比较：<br/>
http://blog.csdn.net/shenbushen/article/details/52140078<br/>

Redis集群部署：<br/>
Linux:http://www.cnblogs.com/wuxl360/p/5920330.html<br/>
Windows: http://www.cnblogs.com/wujixiong/p/6816883.html<br/>

Spring-data-redis Sentinel配置：<br/>
http://blog.csdn.net/qq_34021712/article/details/75949706<br/>
Redis主从集群的Sentinel配置(包括主从集群及其Sentinel集群):<br/>
http://www.cnblogs.com/LiZhiW/p/4851631.html<br/>

spring整合redis(集群、主从)<br/>
http://blog.csdn.net/sunqingzhong44/article/details/70976038?locationNum=6&fps=1<br/>

Memcached安装：<br/>
http://blog.csdn.net/l1028386804/article/details/61417166<br/>
Memcached学习：<br/>
http://www.runoob.com/memcached/memcached-connection.html<br/>

Dubbo框架：<br/>
http://blog.csdn.net/u013142781/article/details/50387583<br/>

IDEA jar打包方式（项目和第三方jar一起打包）：<br/>
https://www.cnblogs.com/qifengshi/p/6036870.html<br/>
http://blog.csdn.net/maozhaoyuan/article/details/52699404<br/>

Flume学习博客:<br/>
http://blog.csdn.net/xiao_jun_0820/article/category/2399621<br/>

PostgresSql数据库相关命令操作：<br/>
https://zhidao.baidu.com/question/524250277168850725.html<br/>
增加主键等 https://www.cnblogs.com/alianbog/p/5598251.html<br/>
修改表的字段类型 http://blog.csdn.net/cdnight/article/details/20281113<br/>

Java实时监控FTP文件变化
https://www.cnblogs.com/duelsol/archive/2013/03/14/2959146.html<br/>

如何运行Jar文件里面main方法：<br/>
http://blog.csdn.net/shymi1991/article/details/50540214<br/>

如何运行Jar包：<br/>
java -jar my-rpc-2.0.jar 127.0.0.1 8888

在linux下如何运行带有第三方jar的Jar程序：
java -cp DBTest.jar:ojdbc6.jar  org.swordfall.DBTest.OracleConnection 

apache 所有开源项目:<br/>
http://archive.apache.org/dist/<br/>

maven三种打包插件（maven-assembly-plugin，maven-shade-plugin与maven-assembly-plugin）：<br/>
https://yq.aliyun.com/articles/308777<br/>
http://blog.csdn.net/defonds/article/details/43233131<br/>
Maven的几个常用plugin：<br/>
https://www.cnblogs.com/zhangxh20/p/6298062.html<br/>

Maven插件库:<br/>
http://maven.apache.org/plugins/index.html<br/>

使用idea 操作数据库时出现的 中文乱码问题:<br/>
https://www.cnblogs.com/bb1008/p/7704458.html<br/>

idea自动补全变量名称和属性名称的快捷键：<br/>
https://www.cnblogs.com/jx17/p/6244504.html<br/>

IntelliJ IDEA如何设置头注释，自定义author和date
https://www.cnblogs.com/gongxin/p/8034606.html<br/>

数据分析博客：<br/>
https://blog.growingio.com/<br/>

java jmx远程监控服务器jvm进程的状况出错：<br/>
>JAVA_OPTS="$JAVA_OPTS
-Dcom.sun.management.jmxremote
-Dcom.sun.management.jmxremote.port=9999 
-Dcom.sun.management.jmxremote.ssl=false 
-Dcom.sun.management.jmxremote.authenticate=false"

参考资料：https://blog.csdn.net/sun_dwl/article/details/79229918<br/>
https://www.iteblog.com/archives/1349.html<br/>

postman是一款网页调试工具，可以发送几乎所有类型的HTTP请求，如Get、Post、Delete等等：<br/>
https://blog.csdn.net/fxbin123/article/details/80428216

java模拟ssh执行shell命令：<br/>
https://blog.csdn.net/u013144287/article/details/77506334

# 数据库选型：
NoSql数据库：
>Mongodb
主要特点：应用程序完善后，模式随之变化（无模式）;支持全索引，实现高性能; 复制和故障切换，实现高可用性；自动分片，易于扩展; 基于丰富文档的查询，易于读取; 主从模式; CAP中的CP
适合于：
(1) 取代Web应用的RDBMS
(2) 半结构化内容管理
(3) 实时分析和高速日志、缓存和高扩展性
(4) Web 2.0、媒体、SaaS和游戏
不适合：
(1) 高度事务型系统
(2) 存在传统数据库需求的应用程序，比如外键约束。

>HBase
主要特点：分布式和可扩展的庞大数据存储系统; 强一致性; 建立在Hadoop HDFS的基础上; CAP中的CP
适合于：
(1)针对读取进行了优化
(2)很适合基于范围的扫描
(3)严格一致性
(4)快速读取和写入，具有可扩展性
不适合于：
(1)典型的事务型应用程序或甚至关系分析
(2)应用程序需要全表扫描
(3)数据需要跨聚合、累积以及跨行分析。

如果数据量有几亿或者几十亿条记录，首选HBase；
如果追求读取性能的话，建议mongodb。


关系型数据库：
>Mysql：

>Postgresql:
