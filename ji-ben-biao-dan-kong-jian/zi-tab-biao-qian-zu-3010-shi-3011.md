# 子tab**标签组**

#### 子tab标签组：

> > 子tab标签组包含两个标签，分别为child\_tab（子tab标签最外层）、child\_tab\_content（子tab标签内容包裹层）

#### child\_tab**标签的属性 :**

> child\_tab标签属性分别如下：
>
> **其中tab\_content\_ids、tab\_content\_titles为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",child\_tab标签的默认size为12
> >
> > **\* tab\_content\_ids ：** tab\_content\_ids属性是child\_tab标签记录包含tab页的id值，即child\_tab\_content标签的id值，必须和child\_tab\_content一一对应，如title="home2,profile2,dropdown12,ddd3"；包含多少tab页，就填写几个id值，注意分隔符
> >
> > **\* tab\_content\_titles ：** tab\_content\_titles属性是child\_tab标签记录包含tab页的title值
> >
> > 如title="home2,profile2,dropdown12,ddd3"；包含多少tab页，就填写几个title值，注意分隔符

#### child\_tab\_content**标签的属性 :**

> child\_tab\_content标签有3个属性分别为为id、name、active；
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **active：** active属性为是否处于选中状态，可以填写的值为“true”，“false”，默认为false

```
 <@child_tab  id="myTab2" tab_content_ids="home,profile,dropdown,ddd" tab_content_titles="home2,profile2,dropdown12,ddd3">
        <@child_tab_content id="home" active="true"> 
            <p>Food truck fixie locavore, accusamus mcsweeney's marfa nulla single-origin coffee squid.</p>
        </@child_tab_content>
        <@child_tab_content id="profile" > 
            <p>Food truck fixie locavore, accusamus mcsweeney's marfa nulla single-origin coffee squid.</p>
        </@child_tab_content>
        <@child_tab_content id="dropdown" > 
            <p>Etsy mixtape wayfarers, ethical wes anderson tofu before they sold out mcsweeney's organic lomo retro fanny pack lo-fi farm-to-table readymade.</p>
        </@child_tab_content>
        <@child_tab_content id="ddd" > 
            <p>hfieiiejjlkfjdsfl.</p>
        </@child_tab_content>
</@child_tab>
```

#### 显示结果 :

![](/assets/tab.png)

