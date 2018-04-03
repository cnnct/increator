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
> > **position: **按钮position属性,用于相对位置\(left：居左、center：居中、right：居右\),默认left
>>
> > **header_have【2.2】: **header_have属性用来控制是否含有标题头，默认"true"
>>
> > **style_type【2.2】: **style_type属性是用来控制panel的风格样式，暂时提供"default"（默认样式），"classical"（经典样式）
> > **icon【2.2】: **icon属性是用来控制panel的标题头的图标，默认没有图标，图标设置参考button标签

#### panel标签的引入方式 :

```
   <@panel id="testPanel" title="标题" position="center">
	<@form id="view_form">
	    <@form_group class="row">
		<@span label="部门联系方式,,2"  value="15706796005"/>
            </@form_group>
        </@form>
    </@panel>
```

#### panel标签的显示结果 :

![](/assets/panel1.png)




