# 子tab**标签组**

#### 子tab标签组：

> > 子tab标签组包含两个标签，分别为child\_tab（子tab标签最外层）、child\_tab\_content（子tab标签内容包裹层）

#### child\_tab**标签的属性 :**

> child\_tab标签有4个属性分别为为id、name、size、title；
>
> **其中title为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",child\_tab标签的默认size为12
> >
> > **title\* ：** title属性是child\_tab标签记录包含tab页的id值，即child\_tab\_content标签的id值，
> >
> > 如title="home2;profile2;dropdown12;ddd3"；包含多少tab页，就填写几个id值，注意分隔符

#### child\_tab\_content**标签的属性 :**

> child\_tab\_content标签有3个属性分别为为id、name、active；
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > **id \* ：** id属性
> >
> > **name ：** name属性
> >
> >**active：** active属性为是否处于选中状态，可以填写的值为“true”，“false”，默认为false

```
 <@child_tab  id="myTab2" title="home2;profile2;dropdown12;ddd3">
        <@child_tab_content id="home2" active="true"> 
            <p>Food truck fixie locavore, accusamus mcsweeney's marfa nulla single-origin coffee squid.</p>
        </@child_tab_content>
        <@child_tab_content id="profile2" > 
            <p>Food truck fixie locavore, accusamus mcsweeney's marfa nulla single-origin coffee squid.</p>
        </@child_tab_content>
        <@child_tab_content id="dropdown12" > 
            <p>Etsy mixtape wayfarers, ethical wes anderson tofu before they sold out mcsweeney's organic lomo retro fanny pack lo-fi farm-to-table readymade.</p>
        </@child_tab_content>
        <@child_tab_content id="ddd3" > 
            <p>hfieiiejjlkfjdsfl.</p>
        </@child_tab_content>
</@child_tab>
```

![](/assets/tab.png)

