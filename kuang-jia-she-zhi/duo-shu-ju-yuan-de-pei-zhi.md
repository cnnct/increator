# 多数据源的使用

#### 一、多数据源配置

#### publicKey、password生成\(即加密\)：

\(1\)cmd打开druid-1.0.18.jar所在文件目录。  
\(2\)执行命令：`java -cp druid-1.0.18.jar com.alibaba.druid.filter.config.ConfigTools 数据库密码`  
\(3\)将得到的publickey、password复制过来即可。

#### 解密：

```
执行com.alibaba.druid.filter.config.ConfigTools.decrypt(publicKey, password)得到密码明文
```

#### 1.db.properties文件配置，有几个数据源就配置几个driver、url、username、password、publicKey，同时还有一个decrypt，指的是数据库密码是否需要解密，示例如下：

```
#datasource1
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://183.129.148.83:3307/manageplat?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=CFIe1ASc5Kb1retmG068HgjTMPPrpgxLBzvQSBXES5EbA4NLmamb45NXPFSyuzP1ApFBQ1fjmWeKrTHwqpqXDw==
publicKey=MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAJRxH4KqChe8kyA2HaEBlM/vOraezJQhw43Ya8WfCQhu6LHXfyWiZqHDMUsLSQaFeYVSWFyINePnuc5IVlil5mUCAwEAAQ==

#datasource2
#jdbc.driver2=oracle.jdbc.driver.OracleDriver
#jdbc.url2=jdbc:oracle:thin:@172.16.200.117:1521:ORCL
#jdbc.username2=manageplat
#jdbc.password2=eyhj9Gg+/9ETYwX2MhDgsH+5HGTd8mhFPZ11Wv9z3UixP+eBiS7Sex49V0KqsYosA09UgrfLNDRz7a5M9tIWwQ==
#publicKey2=MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAJQ7ES+yG/PHawLgQWbjBOpQnrTaQPjtM/cu2FQUt9mKNgJtiHMKkkquFAD6h/ffHAGHznDMN//HPj83YOTfYnsCAwEAAQ==

#decrypt:Does the password need to be decrypted?true--need,else--don't need
decrypt=true
```

#### 2.applicationContext-dao.xml文件配置，有几个数据源就配置几个DruidDataSource、SqlSessionFactoryBean、MapperScannerConfigurer，示例如下：

\(1\)DataSource，多个DataSource配置时一般只需将id、driverClassName、url、username、password修改即可。

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
    <property name="filters" value="config,stat" />
    <property name="connectionProperties" value="config.decrypt=${decrypt};config.decrypt.key=${publicKey}" />
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
    <property name="filters" value="config,stat" />
    <property name="connectionProperties" value="config.decrypt=${decrypt};config.decrypt.key=${publicKey2}" />
</bean>
```

\(2\)SqlSessionFactory，多个SqlSessionFactory配置时只需将id、dataSource修改即可。

```
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="dataSource"></property>
    <property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" />
    <property name="databaseIdProvider" ref="databaseIdProvider"/>
</bean>

<bean id="sqlSessionFactory2" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="dataSource2"></property>
    <property name="configLocation" value="classpath:config/mybatis/SqlMapConfig.xml" />
    <property name="databaseIdProvider" ref="databaseIdProvider"/>
</bean>
```

\(3\)MapperScannerConfigurer，多个MapperScannerConfigurer配置时只需将basePackage、sqlSessionFactoryBeanName修改即可，其中basePackage的value对应逆向工程生成文件时generatorConfig.xml中配置的后两个targetPackage目录，关于此处详情可见本页最后。

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

\(1\)DataSourceTransactionManager

```
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    property name="dataSource" ref="dataSource"></property>
</bean>

<bean id="transactionManager2" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
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

#### 1.generatorConfig.xml文件配置

#### 注：

> * #### 每次使用逆向工程为一个数据源生成文件后，就修改一下driverClass、connectionURL、userId、password、publicKey以及3个targetPackage的值，还有&lt;table&gt;的tableName，配置上需要逆向工程生成文件的表，然后再执行逆向工程GeneratorSqlmap.java。
> * #### 每次运行GeneratorSqlmap.java生成文件时，会自动删除已存在的基础实体类和基础mapper的同名文件，因此使用前一定注意是否这三个文件有做过个性化修改。
> * #### 因此，鉴于前一事项，建议基础实体类和基础的mapper尽量不要去修改，若要修改或增加功能，在custom中进行处理。
> * #### 以上提到的三个基础文件及custom为别为：
>
> /src/com/cnnct/po/表名.java，对应的custom文件：/src/com/cnnct/po/custom/表名Cust.java
>
> /src/com/cnnct/mapper/表名Mapper.java，对应的custom文件：/src/com/cnnct/mapper/custom/表名CustMapper.java
>
> /src/com/cnnct/mapper/表名Mapper.xml，对应的custom文件：/src/com/cnnct/mapper/custom/表名CustMapper.xml

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
            password="${jdbc.password} publicKey="${publicKey}">
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

         <!-- 表配置,如果数据库为oracle,那么，还需要加上schema属性,值为oracle用户名 -->
         <table tableName="bs_city" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false"></table>
         <table tableName="bs_city" schema="manageplat" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false"></table>
         <!-- 自定义数据库中的字段映射的实体类属性类型 -->
         <table tableName="sys_action_log" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false">
             <columnOverride column="message" javaType="java.lang.String" jdbcType="VARCHAR"/>
             <columnOverride column="in_data" javaType="java.lang.String" jdbcType="VARCHAR"/>
             <columnOverride column="out_data" javaType="java.lang.String" jdbcType="VARCHAR"/>
         </table>
    </context>
</generatorConfiguration>
```

#### 2.关于generatorConfig.xml文件中的三个targetPackage目录配置说明

###### 初始单数据源或多数据源的第一个数据源时，三个targetPackage分别默认为：com.cnnct.po、com.cnnct.mapper、com.cnnct.mapper。

###### 如果配置多个数据源或不想用这3个默认目录，修改规则为：在此3个目录的基础上补上一个后缀，后两个目录必须相同。

###### 如：com.cnnct.po2、com.cnnct.mapper2、com.cnnct.mapper2

###### 或 com.cnnct.pooracle、com.cnnct.mapperoracle、com.cnnct.mapperoracle等。

###### 而这里的后两个目录\(相同，即同一个目录\)，对应applicationContext-dao.xml文件中basePackage，通过数据源一一对应。

#### 注：如果使用的不是3个默认目录，那么，注入基础Mapper\(非custom中的\)时，需要使用别名，别名在基础Mapper中有。

#### 示例：

基础Mapper

```
package com.cnnct.mapper;

import org.springframework.stereotype.Component;

import com.cnnct.po.SysRole;

@Component("sysRoleMapperOracle")
public interface SysRoleMapper {
    int deleteByPrimaryKey(Long roleId);

    int insert(SysRole record);

    int insertSelective(SysRole record);

    SysRole selectByPrimaryKey(Long roleId);

    int updateByPrimaryKeySelective(SysRole record);

    int updateByPrimaryKey(SysRole record);
}
```

注入代码，此处为sysRoleMapperOracle对应基础Mapper中的别名，而不能随意起名

```
@Autowired
private SysRoleMapper sysRoleMapperOracle;
```

#### 3.由于oralce中number类型长度的变化，导致生成的实体类的类型变化问题

可以通过修改generatorConfig.xml中的如下配置固定类型：

```
<!-- 默认false，根据数据库中字段类型长度把JDBC DECIMAL 和 NUMERIC 类型解析为对应的类型；为 true时把JDBC DECIMAL 和
    NUMERIC 类型解析为java.math.BigDecimal -->
<javaTypeResolver>
    <property name="forceBigDecimals" value="false" />
</javaTypeResolver>
```



