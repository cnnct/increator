# toast提示**标签**

#### toast**标签的属性 :**

> toast标签有1个属性delay\_time,**毫秒为单位**，引入标签时默认隐藏，需要配合js调用，2秒后自动消失

#### toast标签的引入方式 :

```
  <@toast delay_time="5000"/>

  Toast.show('Custom class alert shown',color);//js代码
  其中color可填的值为danger，info，warning，default，success，默认info
```

#### toast标签的显示结果 :

![](/assets/toast.png)

