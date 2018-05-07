# calendar标签

#### calendar**标签的属性 :**

> calendar标签有2个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性  
> > **size\_type：** 大小类型：默认小，可选big\(大\)、mid\(中\)

#### calendar标签的引入方式 :

```
<@calendar id="demo_calendar"/>
```

```
//清空日历所在div
$('#demo_calendar').html('');
//创建日历
var calendar = createCalendar({id:'demo_calendar','2018-05-06',end:'2018-08-13',selected:['2018-05-07','2018-06-17']});
```

#### calendar标签显示效果图 :



