* ## [font icon规范](/kai-fa-gui-fan/qian-duan-kai-fa-gui-fan.md)font icon规范页面开发规范参考

> 必看！！！！本处不细述，详见bootstrap开发规范： [http://codeguide.bootcss.com/\#html-syntax](http://codeguide.bootcss.com/#html-syntax)

* ## 后端开发规范

> #### 命名规范
>
> > 新增表名、字段名、文件名、类名、方法名、变量名等，使用英文驼峰式或带下划线驼峰式，尽量避免拼音，已存在对象忽略。单词或单词缩写要注意可读性高、简洁明了，单词要用常用单词或缩写，太长的单词要简化成缩写，方便其它同事一目了然。
>
> #### sys\_func表规范
>
> > 功能菜单表sysfunc中菜单规则保持现有递增及上下级编号规则，详见下图所示：![](/assets/sys_func.png)
> >
> > 其中菜单图标样式使用，详见"[font icon规范](/kai-fa-gui-fan/qian-duan-kai-fa-gui-fan.md)"章节
>
> #### 系统类方法名命名规则
>
> > controller类名命名
> >
> > > 业务名+Ctrl，如LoginCtrl.java
> >
> > controller类跳转目标页面方法命名
> >
> > > to+模块名或者菜单名（首字母大写）+操作页面（Index、Add、Edit），如记名卡发卡： toNamedCardSellIndex
> >
> > controller类业务方法名规则
> >
> > > 操作动作（例如save、edit、delete、sell）+模块名（首字母大写）或者菜单名，如saveRole、delRole
> >
> > service类名命名
> >
> > > 业务名+Serv，如LoginServ.java，loginServImpl.java
> >
> > 系统页面文件名命名规则，统一小写
> >
> > > 根据菜单名就可以知道对应的页面。例如：记名卡发卡：namedcard\_sell.ftl，机构管理：organ\_index.ftl   organ\_edit.ftl
>
> #### 系统错误码
>
> > 针对系统代码错误（sys\_code\_err）对应的字段FIELD\_NAME\(类中属性名称\)规范：按目前的全大写，单词间用下划线分隔，如OFFLINE\_ACC\_FREEZE。此规定也适用于sys\_code\_tr表、sys\_code表
>
> #### 代码字典等常量使用
>
> > 代码中使用到code字典变量的地方，都要使用变量方式，不要写成’4’,’2010’这样的，要统一写成Sys\_Code.STATE\_ZX这样的方式。如：
> >
> > ![](/assets/sys_code.png)
>
> #### 系统时间使用
>
> > 涉及到需要手动赋值，保存到库中的时间字段统一获取数据库时间方法，一律使用getDatabaseDate，特殊情况除外，如需要临时记录文件日志中需要输出时间，则可以使用new Date方式。
>
> #### 数字小数位数规范
>
> > 页面上需要展示金额的地方统一格式化到2位小数。特殊情况除外，如话费业务中需要保留三位小数。但数据库中一般精确到分，保存整数。
>
> #### 系统缩写规定：
>
> > 但缩写要注意可读性高、简洁明了，单词要用常用单词缩写，方便其它同事一目了然。包名、文件夹名一定小写，若有必要再加下划线，主要防止linux平台上文件名大小写敏感造成的bug。特别是从小写改成大写，提交vs平台，或者在window环境中覆盖时是不会变更大小写的，然后再用window的代码更新到linux上时，造成异常。
> >
> > 常用缩写如：sys、om、serv、acc等
> >
> > #### 完善注释
> >
> > * ###### 类文件方法名前必须注释说明该方法用途。参数较复杂的方法，除了写方法功能注释，还要补充说明参数用法，方便其它同事使用时直接使用，否则其它同事再使用时，不知道怎么用，就会直接重写一个功能类似的方法，且有可能稳定性还不如老方法，造成一些重复垃圾代码
> >
> > ![](/assets/comment.png)
> >
> > * ###### 在已经完成的功能代码基础上额外再做修改，必须要注释说明改造原因，以便其它同事再使用到这段代码时，能快速理解改造原因，避免漏改、错改、或误删除，格式可如下
> >
> > ![](/assets/comment2.png)
> >
> > * ###### 提交vsts上的源代码，要添加注释说明，不要出现类似于“代码优化”、“错误修改”等模糊概念的敷衍语句，同理适用于svn，正确用法,如下图
> >
> > ###### ![](/assets/vsts_comment.png)
> >
> > ###### ![](/assets/vsts_comment2.png)
> >
> > * #### 日志输出
> >
> > > 去掉无用的System.out.print的打印输出语句，替换为适当使用log4j的日志输出进调试输出。
>
> #### 交易代码、错误码等createcode.java使用规则
>
> > 添加完field\_name后，需要重新生成code，对应的类还是tr\_code.java。若增加了code，只需要重新执行一下，再和业务代码一并提交到vs上，保证上传的代码无编译错误即可。同理可一并生成代码字典sys\_code.java。CreateCode.java可根据实际情况修改
> >
> > >



