# http接口服务使用配置

* 配置server接口类型
  > 1.当需要新建一类接口服务时，需要首先配置一个拦截器：  
  > ![](/assets/httplangjieqipeizhi.png)  
  > 2.在拦截器中初始化业务需要的数据：  
  > ![](/assets/interceptor.png)
  > 3.在ServerAspet类中配置异常时要处理的业务
  > ![](/assets/serverAspet.png)
  > ![](/assets/httpyichangchuli.png)
  > 4.在InterFinallyServImpl类中配置finally要处理的业务
  >

