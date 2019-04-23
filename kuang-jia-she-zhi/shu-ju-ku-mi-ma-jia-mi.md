## 数据库密码加密开关，位于db.properties![](/assets/dbpwd_encrypt.png)

## 数据库密码加密方法

在druid.x.y.z.jar所在的目录进入命令行，执行

```
java -cp druid-1.0.18.jar com.alibaba.druid.filter.config.ConfigTools 密码值
```

将执行结果中的publicKey和password分别拷贝到db.properties对应的项中即可![](/assets/dbpwd_encrypt2.png)

