# button_group**标签**

#### button_group**标签的属性 :**
** 注意：id属性的值和onclick属性的值不能相同，存在冲突 **
> button_group按钮组标签属性分别如下：

> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为1
>>
> > **position: **按钮组的position属性,用于相对位置\(left：居左、center：居中、right：居右\)
>>
>> ** group: ** 按钮组标签的按钮组数据，拥有属性：id,name,size,type,class,position,onclick,data_target,auth_key,color,icon,check_resubmit,title,value等,属性可以参照button标签




#### button_group标签的引入方式 :

```
   <@button_group size="2"
	          group=[
				    {"id":"btn1","value":"查询" ,"icon":"repeat","onclick":"doTest('123')","title":"提示","name":"btn1","auth_key":"btn1"},
				    {"id":"btn2","value":"查询1" ,"icon":"repeat","onclick":"doTest('123')","title":"提示1","name":"btn2","auth_key":"btn2"}
				]/>
```

#### button标签的显示结果 :

![](/assets/button.png)

#### button图标使用，icon="xxxxxx"，值取样式表名称的“-”横线后的字符串，如下图所示

[http://v3.bootcss.com/components/](http://v3.bootcss.com/components/)
* bootstrap默认图标
![](/assets/icon-font03.png)
* font-increator中的扩展图标，【2.0】版本后可用
![](/assets/button1.png)
![](/assets/button2.png)

