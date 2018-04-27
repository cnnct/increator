# span\_table和span\_tr和span\_td**标签**

#### 注：span\_table和span\_tr和span\_td标签为一体的。

#### span\_table**标签的属性 :**

> span\_table标签有2个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：**size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12
> >
> > **label\_color：** 是否启用彩色风格，默认启用

#### span\_tr**标签的属性 :**

> span\_tr标签有1个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12

#### span\_td**标签的属性 :**

> span\_td标签有2个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",当type为label时，默认size为2，当type为value时，默认为10，文本实际宽度计算方式： 1、获取所在列的最大宽度 2、算出label和value各占总宽度的比例 3、以算出的比例得出实际宽度。注意：如果\(label的size最大值a + value的size最大值b\)大于12，那么label的size为a，而value的size为\(12 - a\)。比如：label的size最大值为5，value的size最大值为10，那么label的size为5，value的size为7，最后label占总宽度的5/12，value占总宽度的7/12。
> >
> > **type ：** 文本类型：分为label和value，默认value

#### span\_table和span\_tr和span\_td标签的引入方式 :

```
        <@span_table label_color="true">
            <@span_tr>
                <@span_td type="label">姓名</@span_td>
                <@span_td type="value">张三</@span_td>
            </@span_tr>
            <@span_tr>
                <@span_td type="label">姓名</@span_td>
                <@span_td type="value">张三</@span_td>
            </@span_tr>
        </@span_table>
```

#### span\_table和span\_tr和span\_td标签显示效果图 :

![](/assets/span_table.png)

