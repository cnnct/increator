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

> ①para.properties中修改配置项，注意仔细看配置注释
>
> ```
> #左侧树菜单是否展示常用菜单，默认为true
> often_func_show=true
> #左侧树菜单常用菜单的基本数据配置，可自行修改，用于拼接树菜单json串使用
> #！！！！注意，id:“99”可以按现在的一级菜单规则指定，但不能和已有的sys_func表中的值重复冲突
> often_func_conf={id:"99",text:"常用菜单",parent_id:"",url:"",icon:"increator-shizhong"}
> ```
>
> ②数据库中增加常用菜单数量配置：sys\_para表的OFTEN\_FUNC\_NUM的值，若未设置此参数，默认显示最近10个常用菜单。



