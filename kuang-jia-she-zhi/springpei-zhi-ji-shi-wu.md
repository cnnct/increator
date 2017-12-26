## applicationContxt-dao.xml以下简称dao.xml

此配置文件配置数据库连接方式，使用阿里的jar包连接。

使用db.properties配置数据库连接信息

```
<context:property-placeholder location ="classpath:db.properties"/>
```

db.properties 文件在config文件夹下

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
```

mapper扫描器，要求mapper.xml和mapper.java同名且在一个目录。

![](/assets/dao-mybatis.png)

## applicationContext-service.xml以下简称servcie.xml

在service.xml中主要配置serviceImpl，主要是为了方便管理。

## applicationContext-transation.xml以下简称tran.xml

在tran.xml中配置事务:切入所有的serviceImpl,控制在**方法名前加notran的不启用事务**。

![](/assets/tran.png)

