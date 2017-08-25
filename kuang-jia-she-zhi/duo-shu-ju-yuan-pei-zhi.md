# 多数据源的使用

\#\#\#\# 

一、多数据源配置

\#\#\#\#  1.db.properties文件配置，有几个数据源就配置几个driver、url、username、password，并配置suffix，此suffix用于逆向工程生成包和文件时使用。示例如下：

jdbc.driver=com.mysql.jdbc.Driver

jdbc.url=jdbc:mysql://172.16.200.200:3306/manageplat?useUnicode=true&characterEncoding=utf-8

jdbc.username=root

jdbc.password=123456

jdbc.driver2=oracle.jdbc.driver.OracleDriver

jdbc.url2=jdbc:oracle:thin:@localhost:1521:manageplat

jdbc.username2=root

jdbc.password2=123456

suffix=oracle

\#\#\#\#  2.applicationContext-dao.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：

\(1\)DataSource，多个DataSource配置时只需将id、driverClassName、url、username、password修改即可。

&lt;bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close"&gt;

&lt;property name="driverClassName" value="${jdbc.driver}" /&gt; &lt;property name="url" value="${jdbc.url}" /&gt;

&lt;property name="username" value="${jdbc.username}" /&gt;

&lt;property name="password" value="${jdbc.password}" /&gt;

&lt;!-- 配置初始化大小、最小、最大 --&gt;

&lt;property name="initialSize" value="5" /&gt;

&lt;property name="minIdle" value="1" /&gt;

&lt;property name="maxActive" value="20" /&gt;

&lt;!-- 配置获取连接等待超时的时间 --&gt;

&lt;property name="maxWait" value="60000" /&gt;

&lt;!-- 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒 --&gt;

&lt;property name="timeBetweenEvictionRunsMillis" value="60000" /&gt;

&lt;!-- 配置一个连接在池中最小生存的时间，单位是毫秒 --&gt;

&lt;property name="minEvictableIdleTimeMillis" value="300000" /&gt;

&lt;property name="validationQuery" value="\#{'\#{jdbc.driver}'=='com.mysql.jdbc.Driver'?'SELECT 1':'SELECT 1 FROM DUAL'}" /&gt;

&lt;property name="testWhileIdle" value="true" /&gt;

&lt;property name="testOnBorrow" value="false" /&gt;

&lt;property name="testOnReturn" value="false" /&gt;

&lt;!-- 打开PSCache，并且指定每个连接上PSCache的大小 --&gt;

&lt;property name="poolPreparedStatements" value="true" /&gt;

&lt;property name="maxPoolPreparedStatementPerConnectionSize" value="20" /&gt;

&lt;/bean&gt;

&lt;bean id="dataSource2" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close"&gt;

&lt;property name="driverClassName" value="${jdbc.driver2}" /&gt; &lt;property name="url" value="${jdbc.url2}" /&gt;

&lt;property name="username" value="${jdbc.username2}" /&gt;

&lt;property name="password" value="${jdbc.password2}" /&gt;

&lt;!-- 配置初始化大小、最小、最大 --&gt;

&lt;property name="initialSize" value="5" /&gt;

&lt;property name="minIdle" value="1" /&gt;

&lt;property name="maxActive" value="20" /&gt;

&lt;!-- 配置获取连接等待超时的时间 --&gt;

&lt;property name="maxWait" value="60000" /&gt;

&lt;!-- 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒 --&gt;

&lt;property name="timeBetweenEvictionRunsMillis" value="60000" /&gt;

&lt;!-- 配置一个连接在池中最小生存的时间，单位是毫秒 --&gt;

&lt;property name="minEvictableIdleTimeMillis" value="300000" /&gt;

&lt;property name="validationQuery" value="\#{'\#{jdbc.driver}'=='com.mysql.jdbc.Driver'?'SELECT 1':'SELECT 1 FROM DUAL'}" /&gt;

&lt;property name="testWhileIdle" value="true" /&gt;

&lt;property name="testOnBorrow" value="false" /&gt;

&lt;property name="testOnReturn" value="false" /&gt;

&lt;!-- 打开PSCache，并且指定每个连接上PSCache的大小 --&gt;

&lt;property name="poolPreparedStatements" value="true" /&gt;

&lt;property name="maxPoolPreparedStatementPerConnectionSize" value="20" /&gt;

&lt;/bean&gt;

\(2\)SqlSessionFactory，多个SqlSessionFactory配置时只需将id、dataSource、mapperLocations修改即可，其中mapperLocations的value是将xml文件以及所在目录加了后缀suffix后生成的，第一个数据源目录是mapper、xml文件名类似\*Mapper.xml，加了后缀suffix后，变成了mapperoracle、\*MapperOralce.xml,由于xml文件名对应了java接口名，所有逆向工程生成时用了驼峰命名。

&lt;bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean"&gt;

&lt;property name="dataSource" ref="dataSource"&gt;&lt;/property&gt;

&lt;property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" /&gt;

&lt;property name="databaseIdProvider" ref="databaseIdProvider"/&gt;

&lt;property name="mapperLocations"&gt;

&lt;list&gt;

&lt;value&gt;classpath:com.cnnct.mapper/\*Mapper.xml&lt;/value&gt;

&lt;/list&gt;

&lt;/property&gt;

&lt;/bean&gt;

&lt;bean id="sqlSessionFactory2" class="org.mybatis.spring.SqlSessionFactoryBean"&gt;

&lt;property name="dataSource" ref="dataSource2"&gt;&lt;/property&gt;

&lt;property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" /&gt;

&lt;property name="databaseIdProvider" ref="databaseIdProvider"/&gt;

&lt;property name="mapperLocations"&gt;

&lt;list&gt;

&lt;value&gt;classpath:com.cnnct.mapperoracle/\*MapperOracle.xml&lt;/value&gt;

&lt;/list&gt;

&lt;/property&gt;

&lt;/bean&gt;

\(3\)MapperScannerConfigurer，多个MapperScannerConfigurer配置时只需将basePackage、sqlSessionFactoryBeanName修改即可，其中basePackage的value对应SqlSessionFactory中配置的mapperLocations目录。

&lt;bean class="org.mybatis.spring.mapper.MapperScannerConfigurer"&gt;

&lt;!-- 配置扫描包的路径，如果要扫描多个包，中间使用半角逗号分隔，要求mapper.xml和mapper.java同名且在同一个目录--&gt;

&lt;property name="basePackage" value="com.cnnct.mapper"/&gt;

&lt;!-- 使用sqlSessionFactoryBeanName --&gt;

&lt;property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/&gt;

&lt;/bean&gt;

&lt;bean class="org.mybatis.spring.mapper.MapperScannerConfigurer"&gt;

&lt;!-- 配置扫描包的路径，如果要扫描多个包，中间使用半角逗号分隔，要求mapper.xml和mapper.java同名且在同一个目录--&gt;

&lt;property name="basePackage" value="com.cnnct.mapperoracle"/&gt;

&lt;!-- 使用sqlSessionFactoryBeanName --&gt;

&lt;property name="sqlSessionFactoryBeanName" value="sqlSessionFactory2"/&gt;

&lt;/bean&gt;

#### 3.如果需要用到事务，还需配置applicationContext-transation.xml文件，有几个数据源就配置几个DataSourceTransactionManager、txAdvice、aop:config，示例如下：

\(1\)DataSourceTransactionManager

&lt;bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager"&gt;

&lt;property name="dataSource" ref="dataSource"&gt;&lt;/property&gt;

&lt;/bean&gt;

&lt;bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager"&gt;

&lt;property name="dataSource" ref="dataSource2"&gt;&lt;/property&gt;

&lt;/bean&gt;

\(2\)txAdvice

&lt;tx:advice id="txAdvice" transaction-manager="transactionManager"&gt;

&lt;tx:attributes&gt;

&lt;tx:method name="\*" propagation="REQUIRED"/&gt;

&lt;tx:method name="notran\*" propagation="NOT\_SUPPORTED" /&gt;

&lt;/tx:attributes&gt;

&lt;/tx:advice&gt;

&lt;tx:advice id="txAdvice2" transaction-manager="transactionManager2"&gt;

&lt;tx:attributes&gt;

&lt;tx:method name="\*" propagation="REQUIRED"/&gt;

&lt;tx:method name="notran\*" propagation="NOT\_SUPPORTED" /&gt;

&lt;/tx:attributes&gt;

&lt;/tx:advice&gt;

\(3\)aop:config

&lt;aop:config expose-proxy="true"&gt;

&lt;!-- 切入包下面的所有类的所有方法 不管返回值是什么，不管输入参数是什么 --&gt;

&lt;aop:advisor advice-ref="txAdvice" pointcut="execution\(\* com.cnnct..\*ServImpl.\*\(..\)\)"/&gt;

&lt;/aop:config&gt;

&lt;aop:config expose-proxy="true"&gt;

&lt;!-- 切入包下面的所有类的所有方法 不管返回值是什么，不管输入参数是什么 --&gt;

&lt;aop:advisor advice-ref="txAdvice2" pointcut="execution\(\* com.cnnct..\*ServImpl.\*\(..\)\)"/&gt;

&lt;/aop:config&gt;

#### 二、多数据源逆向工程

\#\#\#\#  1.generatorConfig.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：

