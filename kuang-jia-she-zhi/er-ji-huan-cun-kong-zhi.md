#####二级缓存开启步骤：
* 步骤1：开启缓存总开关
![](/assets/mybatis_cashe.png)
* 步骤2： 由于mybatis的二级缓存是针对单独xml文件的，所以对需要配置二级缓存的文件加入cache标签，mybatis逆向工程会自动默认生成该标签，即支持二级缓存，但其他参数需要自行调控
![](/assets/mybatis_cashe2.png)
参数说明：
![](/assets/mybatis_cache3.png)