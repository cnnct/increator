# select\_list**标签**

#### select\_list**标签的属性 :**

> select\_list标签有10个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > **label：** select框label
> >
> > \***sql\_key：** SQL语句对应的key , 比如：select FILE\_ID,FILE\_ORIG\_NAME from sys\_attachment where FILE\_ID not in \(1,5\)
> >
> >**sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > \***show\_field：** 显示名对应的字段
> >
> > \***value\_field：** 值对应的字段
> >
> > **width：** 标签中select宽度，html中的px为单位
> >
> > **height：** 标签中select高度，html中的px为单位
> >
> > \***onclick：** 添加按钮onclick事件
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",search\_tree标签的默认size为4
> >
> > **cust_get_data_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为string类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >


#### select\_list标签的引入方式 :

```
<@select_list id="demoId" name="demoName" label="组员" onclick="addOption()" sql_key="bs_city2"
      show_field="file_orig_name" value_field="file_id" size="6" width="200" height="300" />
```

然后再写一个对应的onclick方法：

```
function addOption(){
  //此方法名为：select_list标签id+AddOption,传入select框option的value,text
  demoIdAddOption(1,"测试");
}
```

#### select\_list标签显示效果图 :

![](/assets/select_list.png)

