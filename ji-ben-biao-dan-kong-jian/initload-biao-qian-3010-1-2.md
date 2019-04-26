# init\_load**标签**

#### init\_load**标签的属性 :**

> init\_load标签为初始化加载login页面和index页面的框架的主要js、css资源的标签，属性分别如下：
>
> > **type：** type属性有4种类型，分别为：login\_head引入到登录页面的头部,login\_foot引入到登录页面的尾部,index\_head引入到主页面的头部,index\_foot引入到主页面的尾部  
> > **load\_layout【1.5】:** 该属性可以填“true”和“false”,默认“false”,该属性在type=“index\_foot”的情况下才有效，主要针对卡管首界面的界面布局功能，当为true时，即认为采用自定义的界面布局，否则为默认布局
> >
> > #### init\_load标签的引入方式 :

```
 <init_load type='index_foot' load_layout="true"/>
```



