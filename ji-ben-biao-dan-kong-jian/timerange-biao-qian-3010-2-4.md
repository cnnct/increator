# time\_range**标签**

#### date\_time\_range**标签的属性 :**

> date\_time\_range标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",date\_time标签的默认size为4
> >
> > **label：** 标签属性，如果为空说明没有
> >
> > **readonly：**是否只读
> >
> > **format：**日期时间格式，参数如下，理论上任意组合，详情可见[http://www.bootcss.com/p/bootstrap-datetimepicker/](http://www.bootcss.com/p/bootstrap-datetimepicker/)
> >
> > * ss：秒，带前导零的2位数字
> >
> > * mm：分钟，带前导零的2位数字
> >
> > * HH：小时，2位数字带前导零 - 24小时格式
> >
> > * DD：月份的日，带前导零的2位数字
> >
> > * MM：月份的数字表示，带前导零的2位数字
> >
> > * YYYY：一年的全数字表示，4位数字
> >
> > **start：**初始开始时间
> >
> > **end：**初始结束时间
> >
> > **min\_val：**最小可选值
> >
> > **max\_val：**最大可选值
> >
> > **show\_time：**是否显示时间

#### date\_time\_range标签的引入方式 :

```
   <@date_time_range label="范围,,2" size="5" id="demo_date_time_range" format="YYYY-MM-DD HH:mm:ss" start="2018-05-03 03:03:03" end="2018-08-03 05:06:07" min_val="2018-05-06 03:03:03" max_val="2018-08-13 05:06:07" show_time="true"/>
```

#### date\_time\_range标签显示效果图 :

![](/assets/date_time_range.png)

