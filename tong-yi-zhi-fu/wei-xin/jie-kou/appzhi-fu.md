```



/**
*公共方法：微信预支付
* @param request
* @param response
* @param json
*  body 商品描述
*  pay_id商户系统支付订单号
*  tr_amt订单结算金额
*  limit_pay no_credit--指定不能使用信用卡支付
* @return JSONObject
*/
publicstaticString sendPrepay(HttpServletRequest request,HttpServletResponse response,JSONObject json)throwsException;
```



