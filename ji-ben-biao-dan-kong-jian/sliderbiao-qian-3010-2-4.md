# Slider**标签**

#### slider**标签的属性 :**
** 注意：id属性的值和onclick属性的值不能相同，存在冲突 **
> button标签属性分别如下：
>
> **其中value为必填项,下面必填项加上了\*号**；
>
> > ** *id ：** id属性
> >
> > **value：** value属性，为进度条的值，默认0，可以填数值
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12
> >
> > **body_size:** body_size属性为控制尺寸大小，可填值small、large默认small
>>
>> **color: ** 颜色属性，可以填的值为"success"、"danger"、"info"、"warning"、"primary",默认info
>>
>>**style_type:**style_type属性为控制进度条类型，可填值round（圆形进度条），如果不填默认横向进度条

#### button标签的引入方式 :

```
   <@button id="bbs"  size="1" value="查询" icon="search" onclick="ss();" title="提示"/>

   <@button id="dd"  size="1" value="删除" icon="remove" title="提示"/>

   <@button id="rr"  size="1" value="重置" icon="repeat"/>
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

