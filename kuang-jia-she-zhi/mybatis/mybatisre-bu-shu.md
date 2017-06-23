mybatis热部署是为了方便开发调试。

com.cnnct.utils包下的MybatisMapperRefresher.java实现了此功能，需要在applicationContxt-service.xml配置

![](/assets/mybatis-refresher.png)

这样在项目启动的时候，会自动去加载这个类，这个类就启动了一个线程定时去读取xml配置文件，获取文件的大小和修改时间。如果下次读取的时候发现大小或者最后修改时间和之前不一致那么就重新加载配置文件。

![](/assets/mybatis-refresher-path.png)这里是读取的xml配置文件路径。

注意：

intellij 需要增修改xml配置文件之后，切换到xml文件编译后目录才能实现文件的自动编译刷新。

