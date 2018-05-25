异常处理这块是在springmvc里定义的异常处理器，代码中只需要抛出，不用谢try、catch，类上经过实验也不用写throws new Exception方法。

具体例子如下：

例如在登录系统时候抛异常

![](/assets/customException.png)

抛出时传入Result\_Code类中的常量，Result\_Code类是根据数据库中的Sys\_ErrCode表生成的。只要在抛异常时传入对应的错误码，会在自定义异常类中自动去错误码缓存中取出对应的错误。被抛出的异常会被自定义错误异常拦截器拦截（注意：抛异常要抛CustomException异常）。

![](/assets/custException.png)

在错误异常拦截器中判断是否是ajax请求，如果是就返回json，普通请求就返回普通格式数据。

另外如果session不存在是要跳登录页面的，

![](/assets/jump-login.png)

在异常拦截器中对响应的异常进行判断，然后转发到登录页面。因为在错误拦截器中只能跳转html页面，所以，定义了一个controller，通过controller再跳转到登录页面。

