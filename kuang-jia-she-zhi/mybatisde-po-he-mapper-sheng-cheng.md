自动生成po类和mapper类

配置入口：/config/mybatis/generatorConfig.xml，配置如下图所示

![](/assets/generator.png)

生成工具类：com.cnnct.utils.GeneratorSqlmap，执行里面的main方法即可，此方法会同步生成如下内容：

* po的基础实体类，po/custom/下的定制实体类
* mapper的基础dao类以及xml文件，mapper/custom下的自定义dao和xml文件

### 注意，基础实体类和基础的mapper尽量不要去修改，若要修改或增加功能，在custom中进行处理



