# Spring定时任务的使用

#### springmvc-servlet.xml文件配置示例：

```
<!-- 加载spring定时任务扫描注解驱动,并设置线程池数量,这两个线程池数量(pool-size)最好>=定时任务数量 -->

<task:annotation-driven executor="myExecutor" scheduler="myScheduler"/>

<task:executor id="myExecutor" pool-size="2"/>

<task:scheduler id="myScheduler" pool-size="2"/>

<!-- 指定spring定时任务类所在包 -->

<context:component-scan base-package="com.cnnct.task"/>
```

#### 定时任务类示例：

```
// 用于将定时任务时间配置在文件中
@PropertySource("classpath:config/parameter/para.properties")
@Component
public class TestTask {

    /**
     * 使定时任务可以解析${}（用于将cron表达式配置在配置文件中时）
     */
    @Bean
    public static PropertySourcesPlaceholderConfigurer propertyConfigInDev() {
        return new PropertySourcesPlaceholderConfigurer();
    }

    /**
     * 定时任务demo,每隔5秒执行一次
     */
    // @Scheduled(cron = "0/5 * * * * ?")
    @Scheduled(cron = "${test_task_cron}")
    public void execute() throws Exception {
        System.err.println("test!!!");
    }
}
```

2018年优化改造，可以将时间配置改到配置文件中，如下图所示



![](/assets/task1.png)

