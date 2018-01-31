## 目的

> 实现在增长较快的日志表进行分库分表存放，目前基础版本支持SYS\_INTERFACE\_LOG、OUT\_INTERFACE\_LOG、SYS\_TASK\_LOG三张表。

## 重要参数及配置

> ### 入口配置
>
> > ##### config/paramter/para.properties：
> >
> > ```
> > #接口是否记日志，默认true，性能测试时可以不记日志
> > interface_log_control=true
> > ```
>
> ### 数据库配置
>
> > ##### sys\_para表中LOG开头的4个参数，最终解释以数据库实际注释为准
> >
> > ```
> > LOG_SPLIT_TABLE：日志分库分表开关，true为分库分表，false为不分
> > LOG_DB_NAME：日志分表库名，默认值为空，表示日志表存当前主库中
> > LOG_TABLE_GEN_NUMBER：日志分表向后生成数量，与分表规则频次对应，x年，x月，x天
> > LOG_TABLE_NAME_SUFF：日志表分表规则，拼接表名，默认值为空，表示不分表，配置值为：日-yyyyMMdd、月-yyyyMM、年-yyyy
> > ```
> >
> > ##### 存储过程+定时器，放在当前主库中，但需要给当前主库用户分配相应的权限
> >
> > ```
> > oracle：pk_create_object.p_create_split_logtable
> > ```



