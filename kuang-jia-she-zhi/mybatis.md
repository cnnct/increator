mybatis的配置文件是config/mybatis/SqlMapConfig.xml

![](/assets/mybatisconfig.png)

定义别名：

![](/assets/alis.png)

sql语句打印：

![](/assets/printSql.png)

在这儿配置插件类全路径，就可以实现sql打印。

# mybatis的使用：

当生成javabean、mapper、mapper配置文件之后，需要在mapper/custom下创建 XxxxCustMapper、XxxCustMapper.xml，在po/custom下创建XxxCust文件。 XxxCustMapper继承XxxMapper,XxxCustMapper.xml中namespace要是当前文件所在路径例如：com.cnnct.mapper.custom.XxxCustMapper。resultMap可以直接继承XxxMapper.xml中定义的BaseResultMap，例如：

![](/assets/mapper-extends.png)

在serviceImpl使用mapper时使用customMapper,使用@Autowired注入。

![](/assets/service-mapper.png)

![](/assets/mapper-demo.png)

如果要新增方法，需要在custMapper.xml中配置

![](/assets/mybatis-demo2.png)

parameterType :设置传入参数类型

resultType:如果返回值不是自定医德resultMap，那么填入java类型例如：java.lang.String

resultMap:设置传出参数的resultMap的id

![](/assets/mybatis-resultMap.png)

在对应的mapper中,使用select标签的id作为方法名，resultType作为返回值类型，parameterType作为传入参数类型。如果返回值是数组或list集合，可以直接在mapper中把返回值类型放在list呃的泛型中。mybatis会自动将结果集封装进去。

![](/assets/mybatis-mapper-func.png)

## mybatis调用存储过程：

调用存储过程没有返回值：

![](/assets/call-noreturn.png)

mapper:

![](/assets/call-noreturn-mapper.png)

调用存储过程有返回值：

需要定义入参和出参：

![](/assets/mybatis-call-map.png)

在下面配置的paramerMap的id，使用上面配置的id

![](/assets/mybatis-call-return.png)

使用的时候定义一个map，给map设置值，执行完mapper的调用存储过程方法后，直接通xml配置的count作为key取出值。

![](/assets/mybatis-call-test.png)

