所有controlloer都要继承BsesCtrl

![](/assets/ModelAttribute.png)

base中添加@ModelAttribut注解，会在进入controller前先执行这个方法获取sesId。

![](/assets/baseCtrl.png)

可以在controller中直接调用这些方法获取用户session数据。

![](/assets/controller-demo.png)

返回json数据的话在方法名上加@ResponseBody，json数据都要封装在resultData对象中。

如果需要跳转页面的话直接返回String，指定返回页面地址，需要带参数的话，使用model.addAttribute\(\)方法。

