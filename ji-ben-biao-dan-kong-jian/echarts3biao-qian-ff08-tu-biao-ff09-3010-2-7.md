# echarts3**标签**

#### echarts3**标签的属性 :**

> echarts3标签属性如下：
>
> **其中id,option_url为必填项,下面必填项加上了\*号**；
>
> > **\*id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为4
> >
> > **class：** class属性
> >
> > **style:** style属性
> >
> > **\*option_url:** 为后台发送ajax去加载echarts的option数据
> >
> > **position:** 为位置，可以填写的值为left，center，right，默认left
> >
> > **interval_time:** 为定时器刷新时间，单位毫秒，如果有值则实时刷新图表


#### echarts标签的引入方式 :

```
  <@echarts3 
		id="echarts_post" 
		size="6" 
		option_url="${base}/tag/echarts" 
		position="center"
		interval_time="10000"		
		/>
```

#### echarts标签的显示结果 :

![](/assets/echarts1.png)

#### echarts标签后台加载option数据：
![](/assets/echart3.png)
后台写法参照https://oss.sonatype.org/content/repositories/releases/com/github/abel533/ECharts/3.0.0/


