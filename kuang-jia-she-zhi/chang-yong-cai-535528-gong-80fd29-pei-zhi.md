### 首页布局风格目前实现了两种

> * 一种是默认风格default，一级菜单在顶部banner区域
> * 另一种是新版本风格，新卡管使用，暂定名称为card，所有菜单通过左边树菜单展示布局。
>
> 配置方式：para.properties中
>
> ```
> #首页风格，①default：默认风格，一级菜单位于顶部；②card：卡管风格，一级菜单合并在左边树菜单。两个风格主要区别是一级菜单区别
> index_page_style=card
> ```



### 常用菜单配置

> ①para.properties中修改配置项
>
> ②数据库中增加常用菜单数量配置：sys\_para表的OFTEN\_FUNC\_NUM 



