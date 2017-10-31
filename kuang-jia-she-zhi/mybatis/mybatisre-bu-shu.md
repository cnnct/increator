mybatis热部署是为了方便开发调试。

需要在para.properties中配置：

mybatis\_refresh为true时启用，false时禁用。

mybatis\_refresh\_info使用Json格式，key为SqlSessionFactoryBean的beanName，value为\*Mapper\*.xml的目录。

```
#mybatis_refresh: true or false
mybatis_refresh=true
#mybatis_refresh_info: use json: key is SqlSessionFactoryBean's Name; value is *Mapper*.xml's directory
mybatis_refresh_info={"sqlSessionFactory":"com/cnnct/mapper"}
```



