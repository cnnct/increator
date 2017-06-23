## applicationContxt-dao.xml以下简称dao.xml

此配置文件配置数据库连接方式，使用阿里的jar包连接。

使用db.properties配置数据库连接信息

```
<context:property-placeholder location ="classpath:db.properties"/>
```

db.properties 文件在config文件夹下

![](/assets/db-config.png)

mapper扫描器，要求mapper.xml和mapper.java同名且在一个目录。

![](/assets/dao-mybatis.png)

## applicationContext-service.xml以下简称servcie.xml

在service.xml中主要配置serviceImpl，主要是为了方便管理。

## applicationContext-transation.xml以下简称tran.xml

在tran.xml中配置事务:切入所有的serviceImpl,控制在**方法名前加notran的不启用事务**。

![](/assets/tran.png)

