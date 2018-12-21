# Redis使用详解

#### 一、搭建redis服务器

具体步骤可网上搜索

#### 二、项目中配置文件修改

1.打开src/config/spring目录下的context.xml文件，解除&lt;import resource="../../baseconfig/redis.xml"/&gt;的注释。

2.打开src/config/parameter目录下的para.properties文件，将sessionRedis=false改为sessionRedis=true。

3.打开src/config/parameter目录下的redis.properties文件，将hostName和port修改为redis服务器对应的参数值。

