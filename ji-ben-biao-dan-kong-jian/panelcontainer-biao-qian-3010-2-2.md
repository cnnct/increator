# panel_container**标签**

#### panel_container**标签的属性 :**

> panel_container标签，主要用来布局card主页的panel面板，可以对多个panel面板进行布局，属性分别如下：

> > **layout：** 布局属性，该属性有内置属性：colspan(布局占用的列数，总共支持12列，默认1列)，rowspan(行属性，默认1行)
>>




#### button_group标签的引入方式 :

```
   <@button_group size="2"
	          group=[
				    {"id":"btn1","value":"查询" ,"icon":"search","onclick":"doTest('123')","title":"提示","name":"btn1","auth_key":"btn1"},
				    {"id":"btn2","value":"查询1" ,"icon":"search","onclick":"doTest('123')","title":"提示1","name":"btn2","auth_key":"btn2"}
				]/>
```

#### button标签的显示结果 :

![](/assets/button_group1.png)

#### button图标使用，icon="xxxxxx"，值取样式表名称的“-”横线后的字符串，如下图所示

[http://v3.bootcss.com/components/](http://v3.bootcss.com/components/)
* bootstrap默认图标
![](/assets/icon-font03.png)
* font-increator中的扩展图标，【2.0】版本后可用
![](/assets/button1.png)
![](/assets/button2.png)

