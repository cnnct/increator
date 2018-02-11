/\*\*

\*公共方法：微信端扫码支付

\* **@param** request

\* **@param** response

\* **@param** json

\*  body 商品描述

\*  order\_id商户订单号

\*  tr\_amt订单结算金额

\*  limit\_pay no\_credit--指定不能使用信用卡支付

\*  isSl传入true时特约商户扫码支付

\* **@return** JSONObject

\*/

**publicstatic**JSONObject sendWebPrepay\(HttpServletRequest request,HttpServletResponse response,JSONObject json\)**throws**Exception;



