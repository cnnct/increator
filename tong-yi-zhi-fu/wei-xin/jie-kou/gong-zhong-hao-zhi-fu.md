```java
/**
*公共方法：微信公众号支付
@paramrequest
*@paramresponse
*@paramjson
*  body 商品描述
*  pay_id商户系统支付订单号
*  tr_amt订单结算金额
*  limit_pay no_credit--指定不能使用信用卡支付
*  openid用户标识
*@returnJSONObject
*/
publicstaticJSONObject sendH5Prepay(HttpServletRequest request,HttpServletResponse response,JSONObject json)throwsException;
```



