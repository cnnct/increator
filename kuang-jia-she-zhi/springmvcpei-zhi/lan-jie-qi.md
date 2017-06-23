用于在用户操作时判断用户有没有权限访问。

![](/assets/springmvc-interceptor-log.png)创建一个类，实现HandlerInterceptor，并在springmvc配置文件中配置。

然后需要实现三个方法preHandle、postHandle、afterCompletion。

preHandle方法在controller方法执行前执行，postHandler方法在方法执行后回调，afterCompletion方法在视图渲染后执行。

在这里做拦截器，我是调了loginService的校验方法：

![](/assets/loginservice-interceptor.png)如果是start、login、toLogin、logout方法和nofunc开头的方法都不拦截，如果有些方法不需要判断权限，就可以加上nofunc，如果方法需要做权限校验，那么执行judegParmit方法。

用户在登录时，都会先通过operId查之前有没有用户登录，有的话将之前的用户cache清除，再存入当前sessionId 和对应的operId以及当前operId对应的map集合。

如图注释很详细：

![](/assets/login.png)

执行judegParmit方法时通过operId找到对应的用户信息，进行登录。

