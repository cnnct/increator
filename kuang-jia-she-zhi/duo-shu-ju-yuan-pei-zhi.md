# 多数据源的使用

#### db.properties文件配置示例：

jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://172.16.200.200:3306/manageplat?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=123456

jdbc.driver2=oracle.jdbc.driver.OracleDriver
jdbc.url2=jdbc:oracle:thin:@localhost:1521:manageplat
jdbc.username2=root
jdbc.password2=123456

suffix=oracle

#### xml文件配置示例：

