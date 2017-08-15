当创建表时，系统中要同时生成数据库实体类、mapper接口文件，mapper.xml配置文件，如果手动去写，不仅费时间，而且容易出错。那么只需要使用mybatis逆向工程就可以了。

配置文件：

![](/assets/generatorc1.png)

运行文件：

![](/assets/GeneratorSqlmap.png)

在使用时只需要在配置文件中西瓜tableName就可以，如果有大字段（text之类）的，需要添加columnOverride配置。

![](/assets/generator.png)

![](/assets/generatortable.png)运行com.cnnct.utils.GeneratorSqlmap就可以生成了。

生成工具类：com.cnnct.utils.GeneratorSqlmap，执行里面的main方法即可，此方法会同步生成如下内容：

* po的基础实体类，po/custom/下的定制实体类
* mapper的基础dao类以及xml文件，mapper/custom下的自定义dao和xml文件

### 注意，基础实体类和基础的mapper尽量不要去修改，若要修改或增加功能，在custom中进行处理



