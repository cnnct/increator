

```
/**
*公共方法：微信退款申请
* @param json
* transaction_id微信订单号
*  order_id商户订单号
*  refund_order_id商户退款订单号
*  tr_amt订单总金额（分）
*  refund_amt退款总金额（分）
* @return
*/
@SuppressWarnings("rawtypes")
publicstaticMap sendRefund(JSONObject json);
```



```
/**
*公共方法：微信退款申请—特约商户扫码支付的退款
* @param json
* transaction_id微信订单号
*  order_id商户订单号
*  refund_order_id商户退款订单号
*  tr_amt订单总金额（分）
*  refund_amt退款总金额（分）
* @return
*/
@SuppressWarnings("rawtypes")
publicstaticMap sendSlRefund(JSONObject json);
```



