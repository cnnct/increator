# http接口服务使用配置

* 配置server接口类型
  > 1.当需要新建一类接口服务时，需要首先配置一个拦截器：  
  > ![](/assets/httplangjieqipeizhi.png)  
  > 2.在拦截器中初始化业务需要的数据：  
  > ![](/assets/interceptor.png)
  > 3.在ServerAspet类中配置异常时要处理的业务：
  > ![](/assets/serverAspet.png)
  > ![](/assets/httpyichangchuli.png)
  > 4.在InterFinallyServImpl类中配置finally要处理的业务：
  >![](/assets/httpfinallydo.png)
  > 5.实际业务处理：
  >![](/assets/httpversion.png)
  > 注意 :接口上需要指定版本号，当请求固定版本号时url中需要加入版本，当请求的url中没有指定版本号，
  > 则默认请求最新版本的接口,当请求的接口版本号不存在，则向下请求最新的接口
  >6.测试接口:
  >
