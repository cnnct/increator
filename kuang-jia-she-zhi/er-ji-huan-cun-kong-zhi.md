##### 二级缓存开启步骤：

**注意说明：mybatis的二级缓存是针对mapper级的，即各namespace的下mapper的二级缓存各自独立，当某个mapper下的sql进行了update、delete、add等操作，则该mapper下的二级缓存将会清空，需要注意的是:假如mapper1对某一表进行了add、update等操作，在mapper2中再查询该表的数据，则数据将会是旧的数据，而非修改后的数据，除非两个mapper的namespace相同，所以mybatis的二级缓存功能一般不建议使用**

* 步骤1：开启缓存总开关
  ![](/assets/mybatis_cashe.png)
* 步骤2： 由于mybatis的二级缓存是针对单独xml文件的，所以对需要配置二级缓存的文件加入cache标签，mybatis逆向工程会自动默认生成该标签，即支持二级缓存，但其他参数需要自行调控
  ![](/assets/mybatis_cashe2.png)
  参数说明\(对上面的参数扩展的详细说明\)：
  ![](/assets/mybatis_cache3.png)



