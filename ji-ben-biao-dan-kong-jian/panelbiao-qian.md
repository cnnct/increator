# Panel**标签**

#### Panel**标签的属性 :**

> Panel标签有4个属性分别为为id、size、title、position；
>
> **其中value为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为4
> >
> > **title:** title属性为标题属性
>>
> > **position: **按钮position属性,用于相对位置\(left：居左、center：居中、right：居右\)


#### button标签的引入方式 :

```
   <@panel id="testPanel" title="标题" position="center">
	<@form id="view_form">
	    <@form_group class="row">
		<@span label="部门联系方式,,2"  value="15706796005"/>
            </@form_group>
        </@form>
    </@panel>
```

#### button标签的显示结果 :

![](/assets/button.png)

#### button图标使用，icon="xxxxxx"，值取样式表名称的“-”横线后的字符串，如下图所示

[http://v3.bootcss.com/components/](http://v3.bootcss.com/components/)

![](/assets/icon-font03.png)



