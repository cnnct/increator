自动生成po类和mapper类

配置入口：/config/mybatis/generatorConfig.xml，配置如下图所示

![](/assets/generator.png)

生成工具类：com.cnnct.utils.GeneratorSqlmap，执行里面的main方法即可，此方法会同步生成如下内容：

po的基础实体类，po/custom/下的定制实体类

mapper的基础dao类以及xml文件，和mapper/表名Mapper.xml

