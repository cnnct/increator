# Select**标签**

#### select**标签的属性：**

```
      select标签有12个属性分别为为id、name、size、readonly、label、select_more、choice_have、search_have、

            sql_condition、sql_key、value_field、show_field；其中id、sql_key、value_field、show_field为必填项；

      id ： id属性

      name ： name属性

      size ： size为尺寸标签，可以填的数值范围为（1-12），如size="6",select标签的默认size为5

      readonly ： readonly为只读属性，可以填写的数值为"true","false",默认为false

      label : label为select标签的前缀标签属性，如label="name;true;2"；其中label属性中含有三个值，第一个值为前缀标签的名字；

              第二个值为前缀标签是否加红色星号，即必填项标志；第三个值为前缀标签的尺寸，可填的数值范围为（1-12），默认尺寸为1；

              引入方式：label="name;true;2" ; label="name;true" ; label="name" label="name;;2" 即三个值都非必填项

      select_more : select_more
```

#### select标签的引入方式见form标签，必须配合form标签使用



