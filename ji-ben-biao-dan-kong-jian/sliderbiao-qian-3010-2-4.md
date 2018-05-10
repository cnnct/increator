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
>>**style_type:**style_type属性为控制进度条类型，可填值round（圆形进度条），如果不填默认横向进度条样式
>>
>>**data_max:**data_max属性在style_type值为round类型的时候可以填写最大值，即进度条的最大值，默认100
>>
>>**data_step:**data_step属性在style_type值为round类型的时候可以填写步长，默认1




#### slider标签的引入方式 :
				<@slider id="slider1" value="20" body_size="small" color="success"  size="12"/>
				<@slider id="slider2" value="30" body_size="large" color="warning" size="12"/>
				<@slider id="slider3" value="40" body_size="large" color="danger" size="12"/>
				<@slider id="slider4" value="50" body_size="large" color="info" size="12"/>
				<@slider id="slider5" value="60" body_size="large" color="primary" size="12"/>
				
				 <@slider id="slider6" value="20" body_size="small" color="green" style_type="round" size="12" />
							<@slider id="slider6" value="20" body_size="large" color="green" style_type="round" size="12"/>
#### slider标签的显示结果 :

![](/assets/button.png)


