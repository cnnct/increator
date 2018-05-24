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

> span\_td标签有3个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **id ：**div的id属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",当type为label时，默认size为2，当type为value时，默认为10。每一列实际宽度为该列的最大宽度\(如：总共两行，第一行第一列size为5，第二行第一列size为3，那么每行第一列size都为5\) 。注意：如果一行的总size大于或者小于12，那么可能达不到预期的效果，所以不要这么做。
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

