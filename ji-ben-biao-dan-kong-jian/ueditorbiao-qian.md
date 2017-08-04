# ueditor**富文本标签**

#### ueditor**标签的属性 :**

> ueditor标签有2个属性分别为为id、name；
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > ** \*id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size属性,默认大小12
> >
> > **position ：** position属性，可填值left,right,center,默认居中



#### ueditor标签的引入方式 :

```
   <@ueditor id="editor" name="myEditor"/>
```

#### ueditor标签的显示结果 :

![](/assets/ueditor.png)

#### ueditor文件上传配置路径的方法:

* 配置文件： config.json,ftp.properties
* ftp.properties文件配置：

![](/assets/ueditor_pubpath.png)

* config.json文件配置：

![](/assets/ueditor_pubpath2.png)

最终上面图片的访问路径为：http://192.168.1.4:8090/manageplat/pubpic/image/当前时间/处理后的文件名


#### ueditor微信图文编辑器使用:
* 注意微信图文编辑需要注册一个账号或绑定一个账号
![](/assets/ueditor_weixin.png)
![](/assets/ueditor_weixin2.png)
![](/assets/ueditor_weixin3.png)