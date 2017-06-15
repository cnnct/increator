# Select**标签**

#### select**标签的属性**

  select标签有12个属性分别为为id、name、size、readonly、label、select_more、choice_have、

search_have、sql_condition、sql_key、value_field、show_field；其中id、sql_key、value_field、

show_field为必填

项,下面必填项加上了*号；

id * ： id属性

name ： name属性

size ： size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为5

readonly ： readonly为只读属性,可以填写的数值为"true","false",默认为false

label : label为select标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值为

前缀标签的名字；

   第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,可填的数值范围为（1-12）,默认尺寸为     

   1；引入方式：label="name;true;2" ; label="name;true" ; label="name" label="name;;2" 即三个值都

非必填项

select_more : select_more为是否多选,可以填的数值为"true","false",默认为false，和choice_have、

search_have属性配合使用

choice_have : choice_have为是否需要第一项加入“--请选择--”这一项,可以填写的数值为"true","false",默认值

为false,

如果select_more属性为true时,choice_have必须为false,因为当select标签为多选标签时，默认加入了“--前选择--”项

search_have : search_have为是否需要搜索框，该属性在select_more属性为true时可用，可以填写的值

为"true","false",默认false

sql_key  ：sql_key为select标签后台执行的sql的key值，

#### select标签的引入方式见form标签，必须配合form标签使用



