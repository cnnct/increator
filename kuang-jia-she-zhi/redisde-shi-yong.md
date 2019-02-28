# Redis使用详解

#### 一、搭建redis服务器

具体步骤可网上搜索

#### 二、项目中配置文件修改

1.打开src/config/spring目录下的context.xml文件，解除&lt;import resource="../../baseconfig/redis.xml"/&gt;的注释。

2.打开src/config/parameter目录下的para.properties文件，将sessionRedis=false改为sessionRedis=true。

3.打开src/config/parameter目录下的redis.properties文件，将hostName和port修改为redis服务器对应的参数值。

#### 三、新增缓存方法

1、在RedisFactory类中新增一个ValueOperations和一个静态ValueOperations，再在init\(\)方法中将ValueOperations值赋给静态ValueOperations：

![](/assets/redis1.png)

2、在RedisFactory类中新增此ValueOperations的静态get方法：

![](/assets/redis2.png)

3、在RedisUtil类中新增一个ValueOperations：

![](/assets/redis3.png)

4、在RedisUtil类中新增此ValueOperations的静态get、put、remove等方法：

![](/assets/redis4.png)

5、在CacheUtil类中调用此缓存：

![](/assets/redis5.png)

