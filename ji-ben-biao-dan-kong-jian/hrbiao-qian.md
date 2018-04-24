# hr**标签**

#### hr**标签的属性 :**

> hr标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **type：** 横线类型，默认为\(单实线\)，可选值有：dashed\(单虚线\)、doubleLine\(双实线\)、doubleDashed\(双虚线\)、doubleLineTd\(上实下虚线\)、doubleLineBd\(上虚下实线\)
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",date\_time标签的默认size为12

#### date\_time标签的引入方式 :

```
			<div class="row">单实线</div>
			<@hr />
			<div class="row">单虚线</div>
			<@hr type="dashed"/>
			<div class="row">双实线</div>
			<@hr type="doubleLine"/>
			<div class="row">双虚线</div>
			<@hr type="doubleDashed"/>
			<div class="row">上实下虚线</div>
			<@hr type="doubleLineTd"/>
			<div class="row">上虚下实线</div>
			<@hr type="doubleLineBd"/>
```

#### date\_time标签显示效果图 :

![](/assets/hr.png)

