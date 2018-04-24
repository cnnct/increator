# label**标签**

#### label**标签的属性 :**

> label标签属性分别为：
>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",label标签的默认size为1
> >
> > **name ：** name属性
> >
> > **must\_star ：** must\_star 属性为是否加必填标志“\*”，可以填写的值为“true”，“false”，默认为false
> >
>> ** cust_style : ** cust_style属性为自定义风格，当该属性存在时，默认的样式被屏蔽，如：cust_style={"icon":"search","color":"success","cust_size":"lg","style":[{"position_site":"left","arrowed":"left"}]}，其中icon为图标，默认没有图标，color为标签的颜色，默认“default”，可填值参照button组件，cust_size为定义尺寸，可填值：“sm”，“lg”,"xlg",默认“sm”，style为定义标签左右边的凹凸风格，其中position_site为指定位置，可填值：“left”，“right”，arrowed属性为凹凸情况，可填值：“left”，“center”，“right”，默认“center”，如果两边都不指定，则凹凸情况都是“center”

#### 【2.3】版本自定义风格label引入：
    <@label name="lable1" cust_style={"icon":"search","color":"warning","cust_size":"lg","style":[{"position_site":"left","arrowed":"right"},{"position_site":"right","arrowed":"right"}]}>
	</@label>
	<@label name="lable1" cust_style={"icon":"search","color":"success","cust_size":"lg","style":[{"position_site":"left","arrowed":"left"}]}>
	</@label>
#### 【2.3】版本后自定义样式显示风格：

![](/assets/label2.png)

