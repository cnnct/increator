* ## [font icon规范](/kai-fa-gui-fan/qian-duan-kai-fa-gui-fan.md)页面开发规范参考

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
> > 其中菜单图标样式使用，详见**font icon规范章节：**
> >
> > 系统类方法名命名规则

2、

3、 系统类方法名命名规则：

（1）、Action直接跳转页面方法名规则：

to+模块名或者菜单名（首字母大写）+操作页面（Index、Add、Edit）。

卡发卡：记名卡发卡、非记名卡发卡 toNamedCardSellIndex

（2）、Action业务方法名规则：

```
     操作动作（例如save、edit、delete、sell）+模块名（首字母大写）或者菜单名。
```

4、 系统页面文件名命名规则，统一小写：

根据菜单名就可以知道对应的页面。

例如：记名卡发卡：namedcard\_sell.ftl。

机构管理：organ\_index.ftl   organ\_edit.ftl

5、 系统错误代码：

针对系统代码错误（sys\_code\_err）对应的字段FIELD\_NAME\(类中属性名称\)规范：按目前的全大写，单词间用下划线分隔，如OFFLINE\_ACC\_FREEZE。此规定也适用于

6、 代码中使用到code字典变量的地方，都要使用变量方式，不要写成’4’,’2010’这样的，要统一写成Sys\_Code.STATE\_ZX这样的方式。如：

