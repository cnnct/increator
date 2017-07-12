系统自动记录业务或错误日志。

业务日志：

![](/assets/Service-log.png)错误日志：

![](/assets/err-log.png)

因为如果抛异常不会执行拦截器的postHandler方法，所以在postHandler中记录业务日志，在异常拦截器中记录错误日志。

