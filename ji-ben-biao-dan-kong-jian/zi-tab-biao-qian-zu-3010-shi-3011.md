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
> > ** tab\_content\_ids ：** tab\_content\_ids属性是child\_tab标签记录包含tab页的id值，即child\_tab\_content标签的id值，必须和child\_tab\_content一一对应，如title="home2,profile2,dropdown12,ddd3"；包含多少tab页，就填写几个id值，注意分隔符，【2.3】版本后该属性取消，全部由tabs属性来加载
> >
> > ** tab\_content\_titles ：** tab\_content\_titles属性是child\_tab标签记录包含tab页的title值
> >
> > 如title="home2,profile2,dropdown12,ddd3"；包含多少tab页，就填写几个title值，注意分隔符，【2.3】
版本后该属性取消，全部由tabs属性来加载


> > **\* tabs 【2.3】：**在【2.3】版本后tabs属性引入将替代tab_content_ids和tab_content_titles属性
引入方式如：tabs=[{"id":"home","title":"home2","icon":"user","color":"success","icon_position":"right"},{"id":"profile","title":"profile2","icon":"search","color":"success"}]，
其中 id为tab项的 id，title为标题名，icon为 tab的图标，color为图标的颜色，icon_position为图标的位置,默认left


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
> >
> > **src【2.1】: **【2.1】版本后引入tab引入iframe页面，即每一个tab子项被嵌入一个iframe，各自独立页面，不在标签里写入内容

```
【2.1】版本之前示例：
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

【2.1】版本后写法示例：
 <@child_tab  id="myTab2" tab_content_ids="home,profile,dropdown12,ddd3" tab_content_titles="home2,profile2,dropdown12,ddd3">
	        <@child_tab_content id="home" active="true" src="${base}/demo/tag/tabContent1"> 
	        </@child_tab_content>
	        <@child_tab_content id="profile"  src="${base}/demo/tag/tabContent2"> 
	        </@child_tab_content>
        	<@child_tab_content id="dropdown" src="${base}/demo/tag/tabContent3"> 
                </@child_tab_content>
                <@child_tab_content id="ddd" src="${base}/demo/tag/tabContent4"> 
                </@child_tab_content>

 </@child_tab>
```

#### 显示结果 :

![](/assets/tab.png)

