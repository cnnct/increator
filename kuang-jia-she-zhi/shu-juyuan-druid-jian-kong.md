## 在项目的web.xml中增加如下配置即可

```
<!-- Druid内置监控功能,启动项目后在浏览器输入：http://ip:port/项目名/druid/或http://ip:port/项目名/druid/index.html即可访问 -->
  <servlet>
      <servlet-name>DruidStatView</servlet-name>
      <servlet-class>com.alibaba.druid.support.http.StatViewServlet</servlet-class>
      <init-param>
        <!-- 是否允许清空统计数据，不写时默认true -->
        <param-name>resetEnable</param-name>
        <param-value>true</param-value>
        </init-param>
        <init-param>
        <!-- 用户名，用户名和密码可以不写，不写时不需要输入，直接登录 -->
        <param-name>loginUsername</param-name>
        <param-value>druid</param-value>
        </init-param>
        <init-param>
        <!-- 密码 -->
        <param-name>loginPassword</param-name>
        <param-value>123456</param-value>
      </init-param>
  </servlet>
  <servlet-mapping>
      <servlet-name>DruidStatView</servlet-name>
      <url-pattern>/druid/*</url-pattern>
  </servlet-mapping>
```



