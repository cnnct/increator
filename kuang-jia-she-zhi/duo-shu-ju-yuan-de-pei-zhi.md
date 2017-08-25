# 多数据源的使用

#### 一、多数据源配置

#### 1.db.properties文件配置，有几个数据源就配置几个driver、url、username、password，并配置suffix，此suffix用于逆向工程生成包和文件时使用。示例如下：

```
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://172.16.200.200:3306/manageplat?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=123456

jdbc.driver2=oracle.jdbc.driver.OracleDriver
jdbc.url2=jdbc:oracle:thin:@localhost:1521:manageplat
jdbc.username2=root
jdbc.password2=123456

suffix=oracle
```

#### 2.applicationContext-dao.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：

\(1\)DataSource，多个DataSource配置时只需将id、driverClassName、url、username、password修改即可。

```
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
    <property name="driverClassName" value="${jdbc.driver}" /> <property name="url" value="${jdbc.url}" />
    <property name="username" value="${jdbc.username}" />
    <property name="password" value="${jdbc.password}" />
    <!-- 配置初始化大小、最小、最大 -->
    <property name="initialSize" value="5" />
    <property name="minIdle" value="1" />
    <property name="maxActive" value="20" />
    <!-- 配置获取连接等待超时的时间 -->
    <property name="maxWait" value="60000" />
    <!-- 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒 -->
    <property name="timeBetweenEvictionRunsMillis" value="60000" />
    <!-- 配置一个连接在池中最小生存的时间，单位是毫秒 -->
    <property name="minEvictableIdleTimeMillis" value="300000" />
    <property name="validationQuery" value="#{'#{jdbc.driver}'=='com.mysql.jdbc.Driver'?'SELECT 1':'SELECT 1 FROM DUAL'}" />
    <property name="testWhileIdle" value="true" />
    <property name="testOnBorrow" value="false" />
    <property name="testOnReturn" value="false" />
    <!-- 打开PSCache，并且指定每个连接上PSCache的大小 -->
    <property name="poolPreparedStatements" value="true" />
    <property name="maxPoolPreparedStatementPerConnectionSize" value="20" />
</bean>

<bean id="dataSource2" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
    <property name="driverClassName" value="${jdbc.driver2}" /> <property name="url" value="${jdbc.url2}" />
    <property name="username" value="${jdbc.username2}" />
    <property name="password" value="${jdbc.password2}" />
    <!-- 配置初始化大小、最小、最大 -->
    <property name="initialSize" value="5" />
    <property name="minIdle" value="1" />
    <property name="maxActive" value="20" />
    <!-- 配置获取连接等待超时的时间 -->
    <property name="maxWait" value="60000" />
    <!-- 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒 -->
    <property name="timeBetweenEvictionRunsMillis" value="60000" />
    <!-- 配置一个连接在池中最小生存的时间，单位是毫秒 -->
    <property name="minEvictableIdleTimeMillis" value="300000" />
    <property name="validationQuery" value="#{'#{jdbc.driver}'=='com.mysql.jdbc.Driver'?'SELECT 1':'SELECT 1 FROM DUAL'}" />
    <property name="testWhileIdle" value="true" />
    <property name="testOnBorrow" value="false" />
    <property name="testOnReturn" value="false" />
    <!-- 打开PSCache，并且指定每个连接上PSCache的大小 -->
    <property name="poolPreparedStatements" value="true" />
    <property name="maxPoolPreparedStatementPerConnectionSize" value="20" />
</bean>
```

\(2\)SqlSessionFactory，多个SqlSessionFactory配置时只需将id、dataSource、mapperLocations修改即可，其中mapperLocations的value是将xml文件以及所在目录加了后缀suffix后生成的，第一个数据源目录是mapper、xml文件名类似\_Mapper.xml，加了后缀suffix后，变成了mapperoracle、\_MapperOralce.xml,由于xml文件名对应了java接口名，所有逆向工程生成时用了驼峰命名。

```
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="dataSource"></property>
    <property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" />
    <property name="databaseIdProvider" ref="databaseIdProvider"/>
    <property name="mapperLocations">
        <list>
            <value>classpath:com.cnnct.mapper/*Mapper.xml</value>
        </list>
    </property>
</bean>

<bean id="sqlSessionFactory2" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="dataSource2"></property>
    <property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" />
    <property name="databaseIdProvider" ref="databaseIdProvider"/>
    <property name="mapperLocations">
        <list>
            <value>classpath:com.cnnct.mapperoracle/*MapperOracle.xml</value>
        </list>
    </property>
</bean>
```

\(3\)MapperScannerConfigurer，多个MapperScannerConfigurer配置时只需将basePackage、sqlSessionFactoryBeanName修改即可，其中basePackage的value对应SqlSessionFactory中配置的mapperLocations目录。

```
<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
	<!-- 配置扫描包的路径，如果要扫描多个包，中间使用半角逗号分隔，要求mapper.xml和mapper.java同名且在同一个目录-->
	<property name="basePackage" value="com.cnnct.mapper"/>
	<!-- 使用sqlSessionFactoryBeanName -->
	<property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
</bean>

<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
	<!-- 配置扫描包的路径，如果要扫描多个包，中间使用半角逗号分隔，要求mapper.xml和mapper.java同名且在同一个目录-->
	<property name="basePackage" value="com.cnnct.mapperoracle"/>
	<!-- 使用sqlSessionFactoryBeanName -->
	<property name="sqlSessionFactoryBeanName" value="sqlSessionFactory2"/>
</bean>
```

#### 3.如果需要用到事务，还需配置applicationContext-transation.xml文件，有几个数据源就配置几个DataSourceTransactionManager、txAdvice、aop:config，示例如下：

```
(1)DataSourceTransactionManager
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
<property name="dataSource" ref="dataSource"></property>
</bean>
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
<property name="dataSource" ref="dataSource2"></property>
</bean>
```

\(2\)txAdvice

```
<tx:advice id="txAdvice" transaction-manager="transactionManager">
<tx:attributes>
<tx:method name="*" propagation="REQUIRED"/>
<tx:method name="notran*" propagation="NOT_SUPPORTED" />
</tx:attributes>
</tx:advice>
<tx:advice id="txAdvice2" transaction-manager="transactionManager2">
<tx:attributes>
<tx:method name="*" propagation="REQUIRED"/>
<tx:method name="notran*" propagation="NOT_SUPPORTED" />
</tx:attributes>
</tx:advice>
```

\(3\)aop:config

```
<aop:config expose-proxy="true">
<!-- 切入包下面的所有类的所有方法 不管返回值是什么，不管输入参数是什么 -->
<aop:advisor advice-ref="txAdvice" pointcut="execution(* com.cnnct.._ServImpl.*(..))"/>
</aop:config>
<aop:config expose-proxy="true">
<!-- 切入包下面的所有类的所有方法 不管返回值是什么，不管输入参数是什么 -->
<aop:advisor advice-ref="txAdvice2" pointcut="execution(* com.cnnct.._ServImpl.*(..))"/>
</aop:config>
```

#### 二、多数据源逆向工程

#### 1.generatorConfig.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：

#### 注：每次使用逆向工程为一个数据源生成文件后，就修改一下driverClass、connectionURL、userId、password以及3个targetPackage的值，还有&lt;table&gt;的tableName，配置上需要逆向工程生成文件的表，然后再执行逆向工程GeneratorSqlmap.java。

```
<generatorConfiguration>
<properties resource="config/parameter/db.properties"/>
<context id="testTables" targetRuntime="MyBatis3" defaultModelType="flat">
<!-- 生成PO类时序列化 -->
<plugin type="org.mybatis.generator.plugins.SerializablePlugin" />
<commentGenerator>
<!-- 是否去除自动生成的注释 true：是 ： false:否 -->
<property name="suppressAllComments" value="true" />
</commentGenerator>
<!--数据库连接的信息：驱动类、连接地址、用户名、密码 -->
<jdbcConnection driverClass="${jdbc.driver}"
connectionURL="${jdbc.url}" userId="${jdbc.username}"
password="${jdbc.password}">
</jdbcConnection>
<!-- 默认false，把JDBC DECIMAL 和 NUMERIC 类型解析为 Integer，为 true时把JDBC DECIMAL 和
NUMERIC 类型解析为java.math.BigDecimal -->
<javaTypeResolver>
<property name="forceBigDecimals" value="false" />
</javaTypeResolver>
<!-- targetProject:生成PO类的位置 -->
<javaModelGenerator targetPackage="com.cnnct.po"
targetProject=".\src">
<!-- enableSubPackages:是否让schema作为包的后缀 -->
<property name="enableSubPackages" value="false" />
<!-- 从数据库返回的值被清理前后的空格 -->
<property name="trimStrings" value="true" />
</javaModelGenerator>
<!-- targetProject:mapper映射文件生成的位置 -->
<sqlMapGenerator targetPackage="com.cnnct.mapper"
targetProject=".\src">
<!-- enableSubPackages:是否让schema作为包的后缀 -->
<property name="enableSubPackages" value="false" />
</sqlMapGenerator>
<!-- targetPackage：mapper接口生成的位置 -->
<javaClientGenerator type="XMLMAPPER"
targetPackage="com.cnnct.mapper"
targetProject=".\src">
<!-- enableSubPackages:是否让schema作为包的后缀 -->
<property name="enableSubPackages" value="false" />
</javaClientGenerator>
<table tableName="bs_city" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false"></table>
<table tableName="bs_pay_org" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false"></table>
<table tableName="sys_action_log" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false">
<columnOverride column="message" javaType="java.lang.String" jdbcType="VARCHAR"/>
<columnOverride column="in_data" javaType="java.lang.String" jdbcType="VARCHAR"/>
<columnOverride column="out_data" javaType="java.lang.String" jdbcType="VARCHAR"/>
</table>
</context>
</generatorConfiguration>
```



