```
1、新建类继承com.increator.pay.alipay.AlipayNotify，重写handingAfterPaid方法
```

```
/**
*支付成功后的业务处理
* @param object
*/
public void handingAfterPaid(JSONObject object){
String out_trade_no = object.getString("out_trade_no");//商户订单号
String tradeno = object.getString("tradeno");//支付宝交易流水号
Date sendpaydate = object.getDate("sendpaydate ");//支付成功时间
//根据out_trade_no处理订单
}
```

### 2、在web.xml中配置这个servlet

类以com.cnnct.json.AlipayNotify为例，web.xml中增加下面这段

```
<servlet>
<servlet-name>alipayNotify</servlet-name>
<display-name>json servlet</display-name>
<servlet-class>com.cnnct.json.AlipayNotify</servlet-class>
<load-on-startup>1</load-on-startup>
</servlet>
<servlet-mapping>
<servlet-name>alipayNotify</servlet-name>
<url-pattern>/alipayNotify</url-pattern>
</servlet-mapping>
```

### 3、在alipay.properties中配置异步通知地址

```
#异步通知地址
notify_url=http://ip:port/alipayNotify
```



