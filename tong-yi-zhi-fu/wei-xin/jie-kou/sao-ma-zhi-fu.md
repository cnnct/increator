```
/**
*公共方法：微信端扫码支付
* @param request
* @param response
* @param json
*  body 商品描述
*  order_id商户订单号
*  tr_amt订单结算金额
*  limit_pay no_credit--指定不能使用信用卡支付
*  isSl传入true时特约商户扫码支付
* @return JSONObject
*/
publicstaticJSONObject sendWebPrepay(HttpServletRequest request,HttpServletResponse response,JSONObject json)throwsException;
```



