# 多数据源的使用

#### 1.db.properties文件配置，有几个数据源就配置几个driver、url等属性，并配置suffix，此suffix用于逆向工程生成包和文件时使用。示例如下：

jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://172.16.200.200:3306/manageplat?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=123456

jdbc.driver2=oracle.jdbc.driver.OracleDriver
jdbc.url2=jdbc:oracle:thin:@localhost:1521:manageplat
jdbc.username2=root
jdbc.password2=123456

suffix=oracle

#### 2.applicationContext-dao.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
<property name="driverClassName" value="${jdbc.driver}" />         <property name="url" value="${jdbc.url}" />
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
<property name="driverClassName" value="${jdbc.driver2}" />         <property name="url" value="${jdbc.url2}" />
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
<property name="dataSource2" ref="dataSource"></property>
<property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" />
<property name="databaseIdProvider" ref="databaseIdProvider"/>
<property name="mapperLocations">
<list>
<value>classpath:com.cnnct.mapperoracle
/*MapperOracle
.xml</value>
</list>
</property>
</bean>