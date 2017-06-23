当创建表时，系统中要同时生成数据库实体类、mapper接口文件，mapper.xml配置文件，如果手动去写，不仅费时间，而且容易出错。那么只需要使用mybatis逆向工程就可以了。

配置文件：

![](/assets/generatorc1.png)

运行文件：

![](/assets/GeneratorSqlmap.png)

在使用时只需要在配置文件中西瓜tableName就可以，如果有大字段（text之类）的，需要添加columnOverride配置。

![](/assets/generatortable.png)运行GeneratorSqlmap就可以生成了。

