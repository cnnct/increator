/\*\*

\*公共方法：微信退款申请

\* **@param** json

\* transaction\_id微信订单号

\*  order\_id商户订单号

\*  refund\_order\_id商户退款订单号

\*  tr\_amt订单总金额（分）

\*  refund\_amt退款总金额（分）

\* **@return**

\*/

@SuppressWarnings\("rawtypes"\)

**publicstatic**Map sendRefund\(JSONObject json\);

/\*\*

\*公共方法：微信退款申请—特约商户扫码支付的退款

\* **@param** json

\* transaction\_id微信订单号

\*  order\_id商户订单号

\*  refund\_order\_id商户退款订单号

\*  tr\_amt订单总金额（分）

\*  refund\_amt退款总金额（分）

\* **@return**

\*/

@SuppressWarnings\("rawtypes"\)

**publicstatic**Map sendSlRefund\(JSONObject json\);



