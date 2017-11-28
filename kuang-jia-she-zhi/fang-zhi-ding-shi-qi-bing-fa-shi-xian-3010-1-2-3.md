### 框架已实现多台服务器分布式部署时，定时器并发控制。

相关配置及参数如下：

> * sys\_para表的TASK\_LOCK\_TIMEOUT：默认配置24小时，超出24小时锁定的记录，自动解锁，一般肯定是程序异常停止，未正常解锁。
>
> * sys\_task\_lock表
>
> * src\config\spring\applicationContext-service.xm中，在原来的baseServ下方增加定时器加锁相应的业务service配置：
> * > ```
>   > 	<!-- 定时任务加锁 -->
>   > 	<bean id="sysTaskLockServ" class="com.cnnct.module.sysmanager.systasklock.SysTaskLockServImpl"/>
>   > ```
>
> ```
>
>     <bean id="sysTaskLockServ" class="com.cnnct.module.sysmanager.systasklock.SysTaskLockServImpl"/>
> ```



