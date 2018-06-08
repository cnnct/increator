# date\_time**标签**

#### date\_time**标签的属性 :**

> date\_time标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",date\_time标签的默认size为5
> >
> > **label：** 标签属性，如果为空说明没有
> >
> > **value：**input框的value
> >
> > **readonly：**是否只读
> >
> > **format：**日期时间格式，参数如下，理论上任意组合，详情可见[http://www.bootcss.com/p/bootstrap-datetimepicker/](http://www.bootcss.com/p/bootstrap-datetimepicker/)
> >
> > * p：子午线（“am”或“pm”） - 根据区域设置文件
> > * P：子午线大写（“AM”或“PM”） - 根据区域设置文件
> > * s：没有前导零的秒
> > * ss：秒，带前导零的2位数字
> > * i：没有前导零的分钟
> > * ii：分钟，带前导零的2位数字
> > * h：小时无前导零 - 24小时格式
> > * hh：小时，2位数字，带前导零 - 24小时格式
> > * H：小时无前导零 - 12小时格式
> > * HH：小时，2位数字带前导零 - 12小时格式
> > * d：没有前导零的月份的日
> > * dd：月份的日，带前导零的2位数字
> > * m：没有前导零的月份的数字表示
> > * mm：月份的数字表示，带前导零的2位数字
> > * M：一个月的短文本表示，三个字母
> > * MM：一个月的全文表示，例如1月或3月
> > * yy：一年的两位数表示
> > * yyyy：一年的全数字表示，4位数字
> >
> > **max\_val：**最大可选值
> >
> > **min\_val：**最小可选值
> >
> > **ctrl\_max\_id：**其他日期控件id：用于限制其他日期控件的最大可选值,当前日期控件选完时间后触发效果。当前日期控件所选值即为被控制日期控件的最大值。
> >
> > **ctrl\_min\_id：**其他日期控件id：用于限制其他日期控件的最小可选值,当前日期控件选完时间后触发效果。当前日期控件所选值即为被控制日期控件的最小值。
> >
> > **start\_view【2.6】：**开始视图，可选值：0\(分视图\)、1\(时视图\)、2\(日视图\)、3\(月视图\)、4\(年视图\)，可参考[http://www.bootcss.com/p/bootstrap-datetimepicker/](http://www.bootcss.com/p/bootstrap-datetimepicker/)。
> >
> > **end\_view【2.6】：**结束视图，可选值：0\(分视图\)、1\(时视图\)、2\(日视图\)、3\(月视图\)、4\(年视图\)，可参考[http://www.bootcss.com/p/bootstrap-datetimepicker/](http://www.bootcss.com/p/bootstrap-datetimepicker/)。注：当大于start\_view时，值等于start\_view。

#### date\_time标签的引入方式 :

```
   <@date_time id="start_time" name="start_time_name" size="3" label="开始时间" />
```

#### date\_time标签显示效果图 :

![](/assets/date_time.png)

