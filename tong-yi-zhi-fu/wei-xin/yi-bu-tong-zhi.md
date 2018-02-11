> # **1、新建类继承com.increator.pay.tenpay.TenpayNotify，重写handingAfterPaid方法**

```
/**
*支付成功后的业务处理
* @param object
*/
public void handingAfterPaid(JSONObject object){
String out_trade_no = object.getString("out_trade_no");//商户订单号
String tradeno = object.getString("tradeno");//微信交易流水号
Date sendpaydate = object.getDate("sendpaydate ");//支付成功时间
//根据out_trade_no处理订单
}
```

> # **2、在web.xml中配置这个servlet**

类以com.cnnct.json.TenpayNotify为例，web.xml中增加下面这段

&lt;servlet&gt;

&lt;servlet-name&gt;tenpayNotify&lt;/servlet-name&gt;

&lt;display-name&gt;json servlet&lt;/display-name&gt;

&lt;servlet-class&gt;com.cnnct.json.TenpayNotify&lt;/servlet-class&gt;

&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;

&lt;/servlet&gt;

&lt;servlet-mapping&gt;

&lt;servlet-name&gt;tenpayNotify&lt;/servlet-name&gt;

&lt;url-pattern&gt;/tenpayNotify&lt;/url-pattern&gt;

&lt;/servlet-mapping&gt;

> # **3、在tenpay.properties中配置异步通知地址**

\#微信支付异步通知地址

NOTIFY\_URL=[http://ip:port/tenpayNotify](http://ip:port/tenpayNotify)

