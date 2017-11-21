# nav_page**标签**

#### nav_page**标签的属性 :**

> nav_page标签为含有左侧导航页面的标签，属性分别为id、size、title；
>
> **其中id，title为必填项,下面必填项加上了\*号**；
>
> > ***id ：** id属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为4
> >
> > ***title:** title属性为标题属性
> >

#### nav_page标签的引入方式 :
这里例举从一个模块的主页面跳转到需要的导航页面：
1.某一主模块的前端代码：
![](/assets/nav_page1.png)
![](/assets/nav_page3.png)
2.后台跳转页面的代码：
![](/assets/nav_page4.png)
3.导航页代码：


```
   <@button id="bbs"  size="1" value="查询" icon="search" onclick="ss();"/>

   <@button id="dd"  size="1" value="删除" icon="remove"/>

   <@button id="rr"  size="1" value="重置" icon="repeat"/>
```

#### nav_page标签的显示结果 :

![](/assets/button.png)





