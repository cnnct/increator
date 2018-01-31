## 目的

> 实现在增长较快的日志表进行分库分表存放，目前基础版本支持SYS\_INTERFACE\_LOG、OUT\_INTERFACE\_LOG、SYS\_TASK\_LOG三张表。

## 重要参数及配置

> ### 入口配置
>
> > config/paramter/para.properties：
> >
> > ```
> > #接口是否记日志，默认true，性能测试时可以不记日志
> > interface_log_control=true
> > ```



