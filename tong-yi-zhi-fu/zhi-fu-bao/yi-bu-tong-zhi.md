1、新建类继承com.increator.pay.alipay.AlipayNotify，重写handingAfterPaid方法

/\*\*

\*支付成功后的业务处理

\* @param object

\*/

 public void handingAfterPaid\(JSONObject object\){

 String out\_trade\_no = object.getString\("out\_trade\_no"\);//商户订单号

 String tradeno = object.getString\("tradeno"\);//支付宝交易流水号

 Date sendpaydate = object.getDate\("sendpaydate "\);//支付成功时间

 //根据out\_trade\_no处理订单

 }

2、在web.xml中配置这个servlet

类以com.cnnct.json.AlipayNotify为例，web.xml中增加下面这段

&lt;servlet&gt;

&lt;servlet-name&gt;alipayNotify&lt;/servlet-name&gt;

&lt;display-name&gt;json servlet&lt;/display-name&gt;

&lt;servlet-class&gt;com.cnnct.json.AlipayNotify&lt;/servlet-class&gt;

&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;

&lt;/servlet&gt;

&lt;servlet-mapping&gt;

&lt;servlet-name&gt;alipayNotify&lt;/servlet-name&gt;

&lt;url-pattern&gt;/alipayNotify&lt;/url-pattern&gt;

&lt;/servlet-mapping&gt;



3、在alipay.properties中配置异步通知地址

\#异步通知地址

notify\_url=http://ip:port/alipayNotify
