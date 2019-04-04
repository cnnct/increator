# input**标签**

#### input**标签的属性 :**

> input标签属性分别为如下：
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为5
> >
> > **type ：** type属性，默认为“text”
> >
> > **label ：** label为input标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,  
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；  
> > label="name" ；label="name,,2" 即三个值都非必填项，【2.5】版本后在view\_para文件里的must\_star\_position属性可以控制must\_star的加载左右位置，默认left
> >
> > **value  ：** value属性
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **placeholder：** placeholder为input框内提示属性
> >
> > **dyn\_tooltip【2.2】：** dyn\_tooltip属性为input框控制动态格式化提示的属性，id属性必须存在，如：  
> > dyn\_tooltip={"flag":"true","type":"card","cust\_type":"\#\#\# \#\#\# \#\#"}，其中flag属性为开启该属性的开关，默认false，type为格式化类型\(可以填的值为default，card,idcard,phone,tunion\(交通部规范\),chinaunion\(住建部规范\)\)该规范的格式可以自行修改，文件为tag\_dyntooltip\_type.json，cust\_type的类型为自定义格式，“\#”号为替换输入的内容的占位符，如果自定义格式存在时，已自定义格式为主
> >
> > **icon【2.4】：** 为图标属性，如icon={"type":"search","color":"success","position":"right"}  
> > type为图标，默认search，color为图标的颜色，position为图标在input框的位置，可填值left和right，默认left
> >
> > **mask【2.5】：**为控制格式化输入功能，如“999-aaa”,其中9代表0-9，代表a-z和A-Z，详情参照masked input\(百度 \)
> >
> > **email\_tootip【2.5】：** 该属性是为了控制是否开启邮箱输入提示，默认false，可填值true和false

#### input标签的引入方式 :

```
    <@input label="邮编:,true,2" id="name" name="name"  type="text" size="4"  />

    <@input label="邮件:,true,2" id="email" name="email"  type="email" size="4" />
```

#### input标签的显示结果:

![](/assets/input.png)

