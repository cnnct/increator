# Spring定时任务的使用

#### xml文件配置：

        &lt;!-- spring定时任务扫描注解驱动,并设置线程池数量,两个线程池数量\(pool-size\)最好&gt;=定时任务数量 --&gt;

	&lt;task:annotation-driven executor="myExecutor" scheduler="myScheduler"/&gt;

	&lt;task:executor id="myExecutor" pool-size="2"/&gt;

	&lt;task:scheduler id="myScheduler" pool-size="2"/&gt;

    &lt;!-- 指定spring定时任务类所在包 --&gt;

    &lt;context:component-scan base-package="com.cnnct.task"/&gt;

#### 定时任务类示例：

@Component

public class TestTask {



   /\*\*

    \*  定时任务demo,每隔5秒执行一次

    \*/

    @Scheduled\(cron = "0/5 \* \* \* \* ?"\)

    public void execute\(\) {

        // do something

    }

}



